cmake_minimum_required(VERSION 3.15)
project(external-cblosc2)
include (ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DBUILD_PLUGINS:option=ON"
    "-DBUILD_STATIC:option=OFF"
    "-DBUILD_SHARED:option=ON"
    "-DBUILD_TESTS:option=OFF"
    "-DBUILD_BENCHMARKS:option=OFF"
    "-DBUILD_EXAMPLES:option=OFF"
    "-DCMAKE_INSTALL_LIBDIR=lib"
)

ExternalProject_Add(
    blosc2
    GIT_REPOSITORY	https://github.com/Blosc/c-blosc2.git
    GIT_TAG		133bd503d7f968e45bc4af39f24b71ee22b7dd1b	#v2.23.0
    PREFIX		blosc2
    CMAKE_ARGS		"${CMAKE_ARGS}"
)
