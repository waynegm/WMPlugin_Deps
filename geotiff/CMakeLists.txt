cmake_minimum_required(VERSION 3.13)
project(external-geotiff)
include(ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DCMAKE_POLICY_DEFAULT_CMP0074=NEW"
    "-DSQLite3_ROOT:path=${SQLite3_ROOT}"
    "-DPROJ_ROOT:path=${PROJ_ROOT}"
    "-DTIFF_ROOT:path=${TIFF_ROOT}"
    "-DCMAKE_INSTALL_LIBDIR=lib"
    "-DWITH_UTILITIES:BOOL=OFF"
)

ExternalProject_Add(
     geotiff
     URL		https://github.com/OSGeo/libgeotiff/releases/download/1.7.4/libgeotiff-1.7.4.zip
     PREFIX		geotiff
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
)

ExternalProject_Add_StepDependencies(geotiff build libtiff)

