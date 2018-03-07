cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_control)
find_package(catkin REQUIRED)

if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()
