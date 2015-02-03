# project
cmake_minimum_required (VERSION 2.6)
project(libelas)

LIST( APPEND CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake_modules/" )

find_package(HAL 0.1 REQUIRED)
find_package(PbMsgs 0.1 REQUIRED)
find_package(Calibu 0.1 REQUIRED)
find_package(Kangaroo 0.1 REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(OpenCV2 REQUIRED)

include_directories(${HAL_INCLUDE_DIRS})
include_directories(${PbMsgs_INCLUDE_DIRS})
include_directories(${Calibu_INCLUDE_DIRS})
include_directories(${Kangaroo_INCLUDE_DIRS})
include_directories(${EIGEN3_INCLUDE_DIR})
include_directories(${OpenCV2_INCLUDE_DIR})

link_libraries(${HAL_LIBRARIES})
link_libraries(${PbMsgs_LIBRARIES})
link_libraries(${Calibu_LIBRARIES})
link_libraries(${Kangaroo_LIBRARIES})
link_libraries(${OpenCV2_LIBRARIES})

# directories
set(LIBELAS_SRC_DIR src)

# include directory
include_directories("${LIBELAS_SRC_DIR}")

# use sse3 instruction set
SET(CMAKE_CXX_FLAGS "-msse3 -std=c++0x")

# sources
FILE(GLOB LIBELAS_SRC_FILES "src/*.cpp")

# make release version
set(CMAKE_BUILD_TYPE Release)

# build demo program
add_executable(elas ${LIBELAS_SRC_FILES})

