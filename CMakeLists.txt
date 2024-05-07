cmake_minimum_required(VERSION 3.22)

project(some_main)

add_library(some STATIC src/some.h src/some.cpp)

if(NOT DEFINED CMAKE_INSTALL_PREFIX)
    message("-------- no install")
endif()

# install(TARGETS some
#     LIBRARY DESTINATION lib
#     ARCHIVE DESTINATION lib
# )

# install(DIRECTORY src/ DESTINATION include)