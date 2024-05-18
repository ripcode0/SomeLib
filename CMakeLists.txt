cmake_minimum_required(VERSION 3.22)

project(Some)

add_library(Some STATIC src/some.h src/some.cpp) #lib 만 쓰는 라이브러리

#CMAKE_SOURCE_DIR = 루트 디렉토리 ${CMAKE_CURRENT_SOURCE_DIR}
set(LIB_DIR ${CMAKE_SOURCE_DIR}/lib)
set(BIN_DIR ${CMAKE_SOURCE_DIR}/bin)

set_target_properties(Some PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY ${LIB_DIR}
    ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${LIB_DIR}
    ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${LIB_DIR}
)

add_subdirectory(src ${CMAKE_BINARY_DIR}/Some)

set(wglad_LIB_DIR ${CMAKE_SOURCE_DIR}/lib)

add_subdirectory(submodule/wglad)

#add submodule
message("---- sub ${wglad_INC_DIR}")
message("---- sub ${wglad_LIB_DIR}")
#add_subdirectory(submodule/SubProject00)


