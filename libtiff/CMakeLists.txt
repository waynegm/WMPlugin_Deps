cmake_minimum_required(VERSION 3.12)
project(external-libtiff)
include(ExternalProject)

list(APPEND CMAKE_ARGS
    "-DCMAKE_INSTALL_PREFIX:PATH=${CMAKE_INSTALL_PREFIX}"
    "-DCMAKE_PREFIX_PATH:PATH=${CMAKE_PREFIX_PATH}"
    "-DCMAKE_INSTALL_INCLUDEDIR:PATH=${CMAKE_INSTALL_PREFIX}/include"
    "-DCMAKE_TOOLCHAIN_FILE:PATH=${CMAKE_TOOLCHAIN_FILE}"
    "-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}"
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

