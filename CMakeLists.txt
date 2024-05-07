cmake_minimum_required(VERSION 3.22)

project(some_main)

add_library(some STATIC some.h some.cpp)

install(TARGETS some
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
)

install(DIRECTORY src/ DESTINATION include)