cmake_minimum_required(VERSION 3.13)
project(external-mba)
include(ExternalProject)

add_cmake_args()

ExternalProject_Add(
     mba
     URL		https://github.com/ddemidov/mba/archive/refs/tags/0.3.zip
     PREFIX		mba
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	false
     CONFIGURE_COMMAND	""
     BUILD_COMMAND	""
     INSTALL_COMMAND	""
)

install(FILES "${PROJECT_BINARY_DIR}/mba/src/mba/mba/mba.hpp" DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
