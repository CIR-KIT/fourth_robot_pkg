cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_bringup)
find_package(catkin REQUIRED)

catkin_package()

# Install
set(LAUNCH_DIRS launch launch/joy launch/robot launch/sensors)
set(CONFIG_DIRS config/joy config/rviz config/sensors)
set(WAYPOINT_DIRS waypoints/ekiden_final/first waypoints/ekiden_final/second waypoints/gazebo waypoints/kyutech waypoints/tsukuba2016 waypoints/tsukuba2017 waypoints/tsukuba_kenshu_center)

foreach(dir ${CONFIG_DIRS} ${LAUNCH_DIRS} ${})
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

# Test
if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
  roslaunch_add_file_check(launch/joy)
  roslaunch_add_file_check(launch/robot)
  roslaunch_add_file_check(launch/sensors)
endif()
