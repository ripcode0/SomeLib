cmake_minimum_required(VERSION 3.22)

project(Some)

add_library(Some STATIC src/some.h src/some.cpp) #lib 만 쓰는 라이브러리

#CMAKE_SOURCE_DIR = 루트 디렉토리 ${CMAKE_CURRENT_SOURCE_DIR}
set(LIB_DIR ${CMAKE_SOURCE_DIR}/lib)

set_target_properties(Some PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY ${LIB_DIR}
    ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${LIB_DIR}
    ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${LIB_DIR}
)

add_subdirectory(src)


#.1 구성단계

# 2 제네레이트 단계

# 3빌드 단계

#optional
# 4 install 단계

# 5 테스트단계