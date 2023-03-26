# WMPlugin_Deps

A repository for building the dependencies of the WMPlugin OpendTect-Plugins. Currently:

- libtiff: support for the Tag Image File Format (TIFF)
- libgeotiff: support for GeoTiff extension of libtiff
- gpkgio: simple GeoPackage file output

Need to set following:

- PROJ_DIR: path to Proj9 include files and library
- SQLITE_DIR: path to SQLite3 include files and library

Example build:

- Go to where you want to host the source, build and output: cd Build
- Clone the repository: git clone https://github.com/waynegm/WMPlugin_Deps.git
- Make the build folder: mkdir bld/WMPlugin_Deps
- Go to the build folder: cd bld/WMPlugin_Deps
- Configure and generate: cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX:PATH=../../bin/PluginDeps/Release  -DPROJ_DIR:PATH=../../proj9 -DSQLITE_DIR:PATH=../../sqlite3 ../../WMPlugin_Deps
- Build and install the dependencies: make install
