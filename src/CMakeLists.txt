include(CheckIncludeFile)
set(SOURCES
    nfd_common.c
    nfd_common.h
    common.h)

macro(REQUIRE_INCLUDE_FILE path name)
    CHECK_INCLUDE_FILE(${path} ${name})
    if (NOT ${name})
        message(FATAL_ERROR "${path} not found")
    endif ()
endmacro()

# add specific implementations
if (WIN32)
    list(APPEND SOURCES nfd_win.cpp)
elseif (APPLE)
    find_library(APPKIT_LIBRARY AppKit)
    list(APPEND SOURCES nfd_cocoa.m)
elseif (UNIX)
    find_package(PkgConfig)
    pkg_check_modules(GTK3 gtk+-3.0 REQUIRED)
    list(APPEND SOURCES nfd_gtk.c)
elseif (UNIX)
    message(FATAL_ERROR "Cannot detect your system, please report to https://github.com/aarcangeli/nativefiledialog-cmake/issues")
endif ()

add_library(nativefiledialog STATIC ${SOURCES})

target_include_directories(nativefiledialog PUBLIC include)

if (UNIX)
    target_include_directories(nativefiledialog PUBLIC ${GTK3_INCLUDE_DIRS})
endif()
