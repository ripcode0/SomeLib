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


add_library(some STATIC src/some.h src/some.cpp)

target_include_directories(some 
    PUBLIC
    $<BUILD_INTERFACE:${SOME_INC_DIR}>
    $<INSTALL_INTERFACE:include>
)

if(NOT DEFINED CMAKE_INSTALL_PREFIX)
    message("-------- no install")
endif()

get_directory_property(has_parent DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PARENT_DIRECTORY)

if(has_parent)
    set(SOME_LIBRARIES some PARENT_SCOPE)
    set(SOME_INCLUDE_DIR SOME_INC_DIR PARENT_SCOPE)
endif()

set(SOME_LIBRARIES some PARENT_SCOPE)
set(SOME_INCLUDE_DIR SOME_INC_DIR PARENT_SCOPE)

# install(TARGETS some
#     LIBRARY DESTINATION lib
#     ARCHIVE DESTINATION lib
# )

# install(DIRECTORY src/ DESTINATION include)