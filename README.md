# WMPlugin_Deps

A repository for building the dependencies of the WMPlugin OpendTect-Plugins. Currently:

- libtiff: support for the Tag Image File Format (TIFF)
- libgeotiff: support for GeoTiff extension of libtiff
- gpkgio: simple GeoPackage file output

Need to set following:

- SQLite3_ROOT: path to SQLite3 include files and library
- PROJ_ROOT: path to Proj9 include files and library
- TIFF_ROOT: path to custom Tiff installation (if needed)

Example build:

- Go to where you want to host the source, build and output: cd Build
- Clone the repository: git clone https://github.com/waynegm/WMPlugin_Deps.git
- Configure and generate: cmake -S WMPlugin_Deps -B bld/WMPlugin_Deps -G "Ninja Multi-Config" -DCMAKE_INSTALL_PREFIX:PATH=inst/WMPlugin_Deps -DSQLite3_ROOT=...sqlite3 -DPROJ_DIR:PATH=...proj9
- Build and install the dependencies: cmake --build bld/WMPlugin_Deps --config Release
