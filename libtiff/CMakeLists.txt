cmake_minimum_required(VERSION 3.12)
project(external-libtiff)
include(ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DBUILD_SHARED_LIBS:option=ON"
    "-Dtiff-tools:option=OFF"
    "-Dtiff-tests:option=OFF"
    "-Dtiff-contrib:option=OFF"
    "-Dtiff-docs:option=OFF"
    "-DCMAKE_INSTALL_LIBDIR=lib"
    )

ExternalProject_Add(
     libtiff
     URL		https://gitlab.com/libtiff/libtiff/-/archive/v4.5.0/libtiff-v4.5.0.zip
     PREFIX		libtiff
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
)

