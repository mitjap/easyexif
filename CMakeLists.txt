cmake_minimum_required(VERSION 2.8.9)

project(easyexif)

set(CMAKE_BUILD_TYPE Release)

include_directories(include)

set(EASYEXIF_INCLUDE_DIRS
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    CACHE STRING " Easyexif include directories"
)

add_subdirectory(lib)
add_subdirectory(bin)

add_executable(demo
    src/exif.cpp
    src/demo.cpp
)
