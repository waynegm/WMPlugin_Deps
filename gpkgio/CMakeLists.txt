cmake_minimum_required(VERSION 3.12)
project(external-gkgio)
include(ExternalProject)

find_library(
    SQLite3_LIBRARY
    NAMES sqlite3
    PATHS ${SQLITE_DIR}/lib
    NO_DEFAULT_PATH
)

list(APPEND CMAKE_ARGS
    "-DCMAKE_INSTALL_PREFIX:PATH=${CMAKE_INSTALL_PREFIX}"
    "-DCMAKE_PREFIX_PATH:PATH=${CMAKE_PREFIX_PATH}"
    "-DCMAKE_INSTALL_INCLUDEDIR:PATH=${CMAKE_INSTALL_PREFIX}/include"
    "-DCMAKE_TOOLCHAIN_FILE:PATH=${CMAKE_TOOLCHAIN_FILE}"
    "-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}"
    "-DBUILD_SHARED_LIBS:option=ON"
    "-DBUILD_TESTING:option=OFF"
    "-DSQLite3_INCLUDE_DIR:path=${SQLITE_DIR}/include"
    "-DSQLite3_LIBRARY:file=${SQLite3_LIBRARY}"
)

ExternalProject_Add(
     gpkgio
     GIT_REPOSITORY	https://github.com/waynegm/gpkg_io.git
     PREFIX		gpkgio
     CMAKE_ARGS		"${CMAKE_ARGS}"
)

