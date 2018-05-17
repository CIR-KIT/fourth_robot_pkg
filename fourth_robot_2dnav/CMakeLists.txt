cmake_minimum_required(VERSION 2.8.3)
project(fourth_robot_2dnav)
find_package(catkin REQUIRED)

catkin_package()

#############
## Install ##
#############
set(MAP_DIRS map/ekiden_final map/maraton17 map/monotsukuri17 map/nakamura_memorial map/opencampus2017 map/tsukuba01 map/tsukuba2017 map/tsukuba_kenshu_center)
set(LAUNCH_DIRS launch launch/amcl)
set(PARAM_DIRS  params/costmap params/planner params/planner/global params/planner/local)

foreach(dir config ${MAP_DIRS} ${LAUNCH_DIRS} ${PARAM_DIRS})
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)


#############
## Testing ##
#############
if (CATKIN_ENABLE_TESTING)
  find_package(roslaunch REQUIRED)
  roslaunch_add_file_check(launch)
  roslaunch_add_file_check(launch/amcl)
endif()
