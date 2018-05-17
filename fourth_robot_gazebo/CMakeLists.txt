cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_gazebo)
find_package(catkin REQUIRED)

catkin_package()

# Install
foreach(dir config/joy launch launch/joy worlds)
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

# Test
if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
  roslaunch_add_file_check(launch/joy)
endif()
