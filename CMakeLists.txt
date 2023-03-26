cmake_minimum_required(VERSION 3.12)
project(dependencies)

set(PROJ_DIR CACHE PATH "path to PROJ9")
set(SQLITE_DIR CACHE PATH "path to SQLite3")

set (PROJ_INCLUDE_DIR ${PROJ_DIR}/include)
find_library(
    PROJ_LIBRARY
    NAMES proj
    PATHS ${PROJ_DIR}/lib
    NO_DEFAULT_PATH
)

find_library(
    SQLite3_LIBRARY
    NAMES sqlite3
    PATHS ${SQLITE_DIR}/lib
    NO_DEFAULT_PATH
)

add_subdirectory(libtiff)
add_subdirectory(geotiff)
add_subdirectory(gpkgio)
