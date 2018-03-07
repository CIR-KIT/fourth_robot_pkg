cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_driver)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  nav_msgs
  tf
  roscpp
  std_msgs
)

catkin_package(
  CATKIN_DEPENDS geometry_msgs roscpp std_msgs
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(fourth_robot_driver_node
  src/fourth_robot_driver_node.cpp 
  src/fourth_robot_driver_node_wrapper.cpp
)

add_dependencies(fourth_robot_driver_node fourth_robot_driver_generate_messages_cpp)

target_link_libraries(fourth_robot_driver_node
  ${catkin_LIBRARIES}
)

if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()
