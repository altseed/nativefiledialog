cmake_minimum_required(VERSION 3.12)

project(nativefiledialog)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)

add_subdirectory(src)

option(NFD_BUILD_UNIT_TESTS "Build the NFD unit tests" ON)

if (NFD_BUILD_UNIT_TESTS)
	add_subdirectory(test)
endif()