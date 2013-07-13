cmake_minimum_required(VERSION 2.8.9)

project(easyexif)

set(CMAKE_BUILD_TYPE Debug)

include_directories(include)

add_library(${PROJECT_NAME}_LIB
    ${easyexif_SOURCE_DIR}/src/exif.cpp
)
add_executable(${PROJECT_NAME}
    src/exif.cpp
    src/demo.cpp
)

install(
	TARGETS easyexif easyexif_LIB
	RUNTIME DESTINATION bin
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib/static
)

install(
	DIRECTORY include/ 
	DESTINATION include
    FILES_MATCHING PATTERN "*.h"
)

set(EASYEXIF_INCLUDE_DIRS
    ${CMAKE_INSTALL_PREFIX}/include
    CACHE STRING " Easyexif include directories"
)

set(EASYEXIF_LIBRARIES
    ${CMAKE_INSTALL_PREFIX}/lib/static/easyexif_LIB.lib
    CACHE STRING " Easyexif libararies"
)
