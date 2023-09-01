cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(social_worlds)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  actionlib
  gazebo_msgs
  geometry_msgs
  actionlib_msgs
  message_generation
  object_recognition_msgs
)
find_package(gazebo REQUIRED)

################################################################################

#add_action_files(
#  DIRECTORY action
#  FILES
#  Actor.action
#)

add_service_files(
  FILES
  Start.srv
  ActorTrajectory.srv
  Regions.srv
)

add_message_files(
 FILES
 Region.msg
)

generate_messages(
 DEPENDENCIES
 std_msgs
 geometry_msgs
 actionlib_msgs
)

catkin_package(
  CATKIN_DEPENDS
  std_msgs
  geometry_msgs
  actionlib_msgs
  message_runtime
)

################################################################################

include_directories(${catkin_INCLUDE_DIRS})
include_directories(${roscpp_INCLUDE_DIRS})
include_directories(${actionlib_INCLUDE_DIRS})
include_directories(${message_generation_INCLUDE_DIRS})
include_directories(${std_msgs_INCLUDE_DIRS})
include_directories(${geometry_msgs_INCLUDE_DIRS})
include_directories(${actionlib_msgs_INCLUDE_DIRS})
include_directories(${GAZEBO_INCLUDE_DIRS})

link_directories(${GAZEBO_LIBRARY_DIRS})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${GAZEBO_CXX_FLAGS}")

