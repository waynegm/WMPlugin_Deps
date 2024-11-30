cmake_minimum_required(VERSION 3.12)
project(external-gkgio)
include(ExternalProject)

find_library(
    SQLite3_LIBRARY
    NAMES sqlite3
    PATHS ${SQLite3_ROOT}/lib
    NO_DEFAULT_PATH
)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DBUILD_SHARED_LIBS:option=ON"
    "-DBUILD_TESTING:option=OFF"
    "-DSQLite3_INCLUDE_DIR:path=${SQLite3_ROOT}/include"
    "-DSQLite3_LIBRARY:file=${SQLite3_LIBRARY}"
)

ExternalProject_Add(
     gpkgio
     GIT_REPOSITORY	https://github.com/waynegm/gpkg_io.git
     PREFIX		gpkgio
     CMAKE_ARGS		"${CMAKE_ARGS}"
)

