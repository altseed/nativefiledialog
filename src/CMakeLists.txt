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
    REQUIRE_INCLUDE_FILE(windows.h HAS_WINDOWS)
    list(APPEND SOURCES nfd_win.cpp)
elseif (APPLE)
    find_library(APPKIT_LIBRARY AppKit)
    REQUIRE_INCLUDE_FILE(AppKit/AppKit.h HAS_APPKIT)
    list(APPEND SOURCES nfd_cocoa.m)
elseif (UNIX)
    find_package(GTK3 REQUIRED)
    REQUIRE_INCLUDE_FILE(gtk/gtk.h HAS_GTK)
    list(APPEND SOURCES nfd_gtk.c)
elseif (UNIX)
    message(FATAL_ERROR "Cannot detect your system, please report to https://github.com/aarcangeli/nativefiledialog-cmake/issues")
endif ()

add_library(nativefiledialog STATIC ${SOURCES})

target_include_directories(nativefiledialog PUBLIC include)