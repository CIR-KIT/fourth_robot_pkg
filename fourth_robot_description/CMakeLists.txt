cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_description)
find_package(catkin REQUIRED)

catkin_package()

# Install
set(LAUNCH_DIRS launch launch/config)
set(MESH_DIRS meshes/DAE/base meshes/DAE/wheel meshes/DAE/sensors/front_lrf meshes/DAE/front_lrf meshes/DAE/gim30 meshes/DAE/gps meshes/DAE/rear_lrf meshes/STL/base meshes/STL/sensors/front_lrf meshes/STL/front_lrf meshes/STL/gim30 meshes/STL/gps meshes/STL/rear_lrf)
set(URDF_DIRS robots urdf urdf/base urdf/wheel urdf/gim30 urdf/gps urdf/lrf)

foreach(dir ${LAUNCH_DIRS} ${MESH_DIRS} ${URDF_DIRS})
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)

# Test
if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
endif()
