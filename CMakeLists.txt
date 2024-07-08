cmake_minimum_required(VERSION 3.22)

project(starter
        DESCRIPTION "a starter repo for building Universal applications"
	VERSION "0.0.1"
	LANGUAGES C CXX ASM
	HOMEPAGE_URL "https://github.com/stillwater-sc/universal")

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Boost)
if(Boost_FOUND)
	message(STATUS "Boost_INCLUDE_DIR" ${Boost_INCLUDE_DIR})
	include_directories(${Boost_INCLUDE_DIR})
endif(Boost_FOUND)

set(STARTER_ROOT_DIR ${PROJECT_SOURCE_DIR})
set(STARTER_INSTALL_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/include)
set(STARTER_INSTALL_LIB_DIR ${PROJECT_SOURCE_DIR}/lib)
set(STARTER_INSTALL_BIN_DIR ${PROJECT_SOURCE_DIR}/bin)

add_definitions(-D UNIVERSAL_ENABLE_TEST=OFF)

# include file for common includes 
include_directories(${STARTER_INSTALL_INCLUDE_DIR})

enable_testing()
#include(CTest)

# Universal is a C++ header-only library, so we do not need to build anything
# if you do add this line, you will get all the Universal regression tests,
# playground, education, applications, and command line utilities.
# You can only add this build subdirectory to ONE and only ONE project
# within the starter workspace. Multiple includes will yield multiple definitions
# of build, install, and uninstall targets.
#add_subdirectory(${STARTER_ROOT_DIR}/ext/stillwater-sc/universal build_universal) 

# MTL4 is a C++ header-only library, so we do not need to build anything
#add_subdirectory(${STARTER_ROOT_DIR}/ext/stillwater-sc/mtl4 build_mtl4) 

add_subdirectory(src)
