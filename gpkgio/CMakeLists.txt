cmake_minimum_required(VERSION 3.15)
project(external-gkgio)
include(ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DSQLite3_ROOT:path=${SQLite3_ROOT}"
    "-DBUILD_TESTING:option=OFF"
)

ExternalProject_Add(
     gpkgio
     GIT_REPOSITORY	https://github.com/waynegm/gpkg_io.git
     PREFIX		gpkgio
     CMAKE_ARGS		"${CMAKE_ARGS}"
)

