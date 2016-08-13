cmake_minimum_required (VERSION 2.6)
project(densecrf)
# -Wall
# -Wno-unused-variable
set(CMAKE_CXX_FLAGS "-Wno-unused-function -Wno-unused-result -Wno-unused-variable -Wno-unused-but-set-variable -Wno-write-strings -Wno-deprecated -Wno-deprecated-declarations -Werror")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fPIC") # Compare speed to direct inclusion
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -msse -msse2 -msse3")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3") # Test -Ofast
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR}/cmake)

find_package(Eigen3 REQUIRED)

include_directories(${EIGEN3_INCLUDE_DIR})
include_directories( include )

add_subdirectory (src)
#add_subdirectory (examples)
add_subdirectory (external)
#add_subdirectory ("Object Segmentation")


file(GLOB_RECURSE showfiles *.cpp *.h *.cc *.hpp *.c *.m)
add_custom_target(showthings SOURCES ${showfiles})
