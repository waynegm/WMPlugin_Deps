cmake_minimum_required(VERSION 3.13)
project(external-nanoflann)
include(ExternalProject)

add_cmake_args()

ExternalProject_Add(
     nanoflann
     URL		https://github.com/jlblancoc/nanoflann/archive/refs/tags/v1.7.0.zip
     PREFIX		nanoflann
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
     CONFIGURE_COMMAND	""
     BUILD_COMMAND	""
     INSTALL_COMMAND	""
)

install(FILES "${PROJECT_BINARY_DIR}/nanoflann/src/nanoflann/include/nanoflann.hpp" DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
