    # Minumum build script for building the Tuvok library needed for Tuvok Commandline UVF converter

cmake_minimum_required(VERSION 3.1 FATAL_ERROR)
project(TuvokDataConverter VERSION 3.1.0)

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/CMake
  ${CMAKE_SOURCE_DIR}/CMake/common)

include(GitExternal)

set(TuvokDataConverter_DESCRIPTION "Tuvok UVF data converter")
set(COMMON_PROJECT_DOMAIN ch.epfl.bluebrain)

include(Common)

common_find_package(Tuvok)

set(TUVOKDATACONVERTERCOMPILE_FLAGS "-std=c++11 -fno-strict-aliasing")
set(TUVOKDATACONVERTER_INCLUDES ${TUVOK_INCLUDE_DIR})

set(TUVOKDATACONVERTER_SOURCES ${CMAKE_SOURCE_DIR}/main.cpp
                               ${CMAKE_SOURCE_DIR}/DebugOut/HRConsoleOut.cpp )

set(TUVOKDATACONVERTER_LINK_LIBRARIES ${TUVOK_LIBRARY})

common_application(tuvokDataConverter)
