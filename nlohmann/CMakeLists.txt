cmake_minimum_required(VERSION 3.5)
project(external-nlohmann)
include(ExternalProject)

add_cmake_args()
list(APPEND CMAKE_ARGS
    "-DJSON_BuildTests:option=OFF"
)

ExternalProject_Add(
     nlohmann
     URL		https://github.com/nlohmann/json/releases/download/v3.12.0/json.tar.xz
     PREFIX		nlohmann
     CMAKE_ARGS		"${CMAKE_ARGS}"
     DOWNLOAD_EXTRACT_TIMESTAMP	ON
)


