cmake_minimum_required(VERSION 2.8.3)
project(track_pkg)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -Wextra -pedantic -O2 -Wno-long-long -fno-omit-frame-pointer")

find_package(catkin REQUIRED COMPONENTS
  cv_bridge
  image_transport
  roscpp
  sensor_msgs
  std_msgs
  geometry_msgs
)

find_package(OpenCV REQUIRED)

if(NOT WIN32)
ADD_DEFINITIONS("-std=c++0x -O3")
endif(NOT WIN32)

catkin_package(
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

link_directories ( ${OpenCV_LIB_DIR} )
MESSAGE(STATUS "OpenCV_LIB_DIR: ${OpenCV_LIB_DIR}")

include_directories ( ${OpenCV_INCLUDE_DIRS} )
MESSAGE(STATUS "OpenCV_INCLUDE_DIRS: ${OpenCV_INCLUDE_DIRS}")

INCLUDE_DIRECTORIES( ${CMAKE_BINARY_DIR}/)
include_directories(${CMAKE_SOURCE_DIR}/src/)

FILE(GLOB_RECURSE sourcefiles "src/*.cpp")

add_executable( kcf_node ${sourcefiles} )
target_link_libraries( kcf_node ${OpenCV_LIBRARIES} ${OpenCV_LIBS} ${catkin_LIBRARIES})

