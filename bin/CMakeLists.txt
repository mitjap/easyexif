#include_directories(${easyexif_SOURCE_DIR}/src)

set(LIB_NAME ${PROJECT_NAME}_DLL)

add_library(${LIB_NAME} SHARED
    ${easyexif_SOURCE_DIR}/src/exif.cpp
)

# copy dll file to bin folder
ADD_CUSTOM_COMMAND (
        TARGET     ${LIB_NAME}
        POST_BUILD
        COMMAND    ${CMAKE_COMMAND}
        ARGS       -E copy_if_different
            ${CMAKE_CURRENT_BINARY_DIR}/${LIB_NAME}.dll
            ${CMAKE_CURRENT_SOURCE_DIR}/${LIB_NAME}.dll
)


set(EASYEXIF_BINARIES
    ${CMAKE_CURRENT_SOURCE_DIR}/${LIB_NAME}.dll
    CACHE STRING " Easyexif binaries (DLLs)"
)
