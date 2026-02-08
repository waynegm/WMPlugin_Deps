cmake_minimum_required(VERSION 3.13)
project(external-eigen)
include(ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DEIGEN_BUILD_TESTING:BOOL=OFF"
    "-DEIGEN_BUILD_BLAS:BOOL=OFF"
    "-DEIGEN_BUILD_LAPACK:BOOL=OFF"
    "-DEIGEN_BUILD_BTL:BOOL=OFF"
    "-DEIGEN_BUILD_SPBENCH:BOOL=OFF"
    "-DEIGEN_BUILD_DOC:BOOL=OFF"
    "-DEIGEN_BUILD_DEMOS:BOOL=OFF"
)

ExternalProject_Add(
     eigen
     URL		https://gitlab.com/libeigen/eigen/-/archive/3.4.1/eigen-3.4.1.zip
     PREFIX		eigen
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
)


