cmake_minimum_required(VERSION 3.22)

#about warning PROJECT_VERSION
cmake_policy(SET CMP0048 NEW)

#allow the IN LIST in IF()
cmake_policy(SET CMP0057 NEW)

if(CMAKE_VERSION VERSION_GREATER 3.8)
    #enalbe the IPO for cmake version that support it
    cmake_policy(SET CMP0069 NEW)
endif()

project(SOME VERSION 0.0.0 LANGUAGES C CXX)

set(SOME_DIR "${CMAKE_CURRENT_SOURCE_DIR}")
set(SOME_INC_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src")
option(SOME_EXPORT "Export Enable" ON)

add_library(some STATIC src/some.h src/some.cpp)

target_include_directories(some 
    PUBLIC
    $<BUILD_INTERFACE:${SOME_INC_DIR}>
    $<INSTALL_INTERFACE:include>
)

message(STATUS "[SOME] pure inc ${SOME_INC_DIR}")

if(NOT DEFINED CMAKE_INSTALL_PREFIX)
    message("-------- no install")
endif()


message(STATUS "[SOME] inc dir : ${SOME_INCLUDE_DIR}")

install(TARGETS some
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)

install(DIRECTORY src/ DESTINATION include/some FILES_MATCHING PATTERN "*.h")

add_subdirectory(submodule/SubProject00)