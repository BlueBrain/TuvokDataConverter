    # Minumum build script for building the Tuvok library needed for Tuvok Commandline UVF converter

cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(TuvokDataConverter)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/CMake
  ${CMAKE_SOURCE_DIR}/CMake/common)

include(GitExternal)

set(VERSION_MAJOR "3")
set(VERSION_MINOR "1")
set(VERSION_PATCH "0")
set(VERSION_ABI 3) # OFF or ABI version

set(LIVRE_DESCRIPTION "Tuvok UVF data converter")
set(COMMON_PROJECT_DOMAIN ch.epfl.bluebrain)

include(Common)

common_package(Tuvok)

set(TUVOKDATACONVERTERCOMPILE_FLAGS "-std=c++11 -fno-strict-aliasing")
set(TUVOKDATACONVERTER_INCLUDES ${TUVOK_INCLUDE_DIR})

set(TUVOKDATACONVERTER_SOURCES ${CMAKE_SOURCE_DIR}/main.cpp
                               ${CMAKE_SOURCE_DIR}/DebugOut/HRConsoleOut.cpp )

set(TUVOKDATACONVERTER_LINK_LIBRARIES ${TUVOK_LIBRARY})

common_application(tuvokDataConverter)
