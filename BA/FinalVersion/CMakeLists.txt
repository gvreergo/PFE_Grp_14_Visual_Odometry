cmake_minimum_required(VERSION 2.8)
project(BAPoseGraph)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++11 -O2")

list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake_modules)

# Eigen
include_directories("/usr/include/eigen3")

# sophus 
find_package(Sophus REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})

# g2o 
find_package(G2O REQUIRED)
include_directories(${G2O_INCLUDE_DIRS})

add_executable(BAPoseGraph BAPoseGraph.cpp)
target_link_libraries(BAPoseGraph
        g2o_core g2o_stuff g2o_types_slam3d ${CHOLMOD_LIBRARIES}
        )


