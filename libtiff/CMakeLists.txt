cmake_minimum_required(VERSION 3.9)
project(external-libtiff)
include(ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DCMAKE_INSTALL_LIBDIR=lib"
    "-Dtiff-tools:option=OFF"
    "-Dtiff-tests:option=OFF"
    "-Dtiff-contrib:option=OFF"
    "-Dtiff-docs:option=OFF"
    )

ExternalProject_Add(
     libtiff
     URL		https://download.osgeo.org/libtiff/tiff-4.7.0.zip
     PREFIX		libtiff
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
)

