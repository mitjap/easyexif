#include_directories(${easyexif_SOURCE_DIR}/src)

set(LIB_NAME ${PROJECT_NAME}_LIB)

add_library(${LIB_NAME} STATIC
    ${easyexif_SOURCE_DIR}/src/exif.cpp
)

# copy lib file to lib folder
ADD_CUSTOM_COMMAND (
        TARGET     ${LIB_NAME}
        POST_BUILD
        COMMAND    ${CMAKE_COMMAND}
        ARGS       -E copy_if_different
            ${CMAKE_CURRENT_BINARY_DIR}/${LIB_NAME}.lib
            ${CMAKE_CURRENT_SOURCE_DIR}/${LIB_NAME}.lib
)


set(EASYEXIF_LIBRARIES
    ${CMAKE_CURRENT_SOURCE_DIR}/${LIB_NAME}.lib
    CACHE STRING " Easyexif libararies"
)
