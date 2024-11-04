cmake_minimum_required(VERSION 3.15)
project(dependencies)

set(SQLite3_ROOT CACHE PATH "path to SQLite3")
set(PROJ_ROOT CACHE PATH "path to PROJ9")
set(TIFF_ROOT CACHE PATH "path to TIFF")

macro( add_cmake_args )

    list(APPEND CMAKE_ARGS
	"-DCMAKE_INSTALL_PREFIX:PATH=${CMAKE_INSTALL_PREFIX}"
	"-DCMAKE_PREFIX_PATH:PATH=${CMAKE_PREFIX_PATH}"
	"-DCMAKE_INSTALL_INCLUDEDIR:PATH=${CMAKE_INSTALL_PREFIX}/include"
	"-DCMAKE_TOOLCHAIN_FILE:PATH=${CMAKE_TOOLCHAIN_FILE}"
    )

    if ( DEFINED CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES )
	list(APPEND CMAKE_ARGS "-DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}" )
    endif()

endmacro(add_cmake_args)

add_subdirectory(libtiff)
add_subdirectory(geotiff)
add_subdirectory(gpkgio)
