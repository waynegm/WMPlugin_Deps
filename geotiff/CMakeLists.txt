cmake_minimum_required(VERSION 3.12)
project(external-geotiff)
include(ExternalProject)

find_library(
    TIFF_LIBRARY
    NAMES tiff
    PATHS ${CMAKE_INSTALL_PREFIX}/lib
    NO_DEFAULT_PATH
)

set (PROJ_INCLUDE_DIR ${PROJ_DIR}/include)
find_library(
    PROJ_LIBRARY
    NAMES proj
    PATHS ${PROJ_DIR}/lib
    NO_DEFAULT_PATH
)

list(APPEND CMAKE_ARGS
    "-DCMAKE_INSTALL_PREFIX:PATH=${CMAKE_INSTALL_PREFIX}"
    "-DCMAKE_PREFIX_PATH:PATH=${CMAKE_PREFIX_PATH}"
    "-DGEOTIFF_INCLUDE_SUBDIR:STRING=include"
    "-DCMAKE_TOOLCHAIN_FILE:PATH=${CMAKE_TOOLCHAIN_FILE}"
    "-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}"
    "-DBUILD_SHARED_LIBS:option=ON"
    "-DPROJ_INCLUDE_DIR:path=${PROJ_INCLUDE_DIR}"
    "-DPROJ_LIBRARY:file=${PROJ_LIBRARY}"
    "-DTIFF_INCLUDE_DIR:path=${CMAKE_INSTALL_PREFIX}/include"
    "-DTIFF_LIBRARY:file=${TIFF_LIBRARY}"
    "-DWITH_UTILITIES:BOOL=OFF"
    )

ExternalProject_Add(
     geotiff
     URL		https://github.com/OSGeo/libgeotiff/releases/download/1.7.1/libgeotiff-1.7.1.zip
     PREFIX		geotiff
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
 )
ExternalProject_Add_StepDependencies(geotiff build libtiff)

