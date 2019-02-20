cmake_minimum_required(VERSION 2.8.3)
project(gazebo_depth_camera_tests)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS roscpp
                                        std_msgs
                                        sensor_msgs
                                        geometry_msgs
                                        tf2_msgs
                                        visualization_msgs
                                        common_robotics_utilities
                                        voxelized_geometry_tools)
find_package(Eigen3 REQUIRED)
set(Eigen3_INCLUDE_DIRS ${EIGEN3_INCLUDE_DIR})

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## LIBRARIES: libraries you create in this project
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project
catkin_package(CATKIN_DEPENDS
               roscpp
               std_msgs
               sensor_msgs
               geometry_msgs
               tf2_msgs
               visualization_msgs
               common_robotics_utilities
               voxelized_geometry_tools
               DEPENDS
               Eigen3)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(SYSTEM ${catkin_INCLUDE_DIRS} ${Eigen3_INCLUDE_DIRS})

## Build options
add_compile_options(-std=c++11)
add_compile_options(-Wall)
add_compile_options(-Wextra)
add_compile_options(-Werror)
add_compile_options(-Wconversion)
add_compile_options(-Wshadow)
add_compile_options(-O3)
add_compile_options(-g)
add_compile_options(-flto)
add_compile_options(-Werror=non-virtual-dtor)

# Mark launch files for installation
install(DIRECTORY launch/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
    PATTERN ".svn" EXCLUDE)

## Mark config files for installation
install(DIRECTORY config/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/config
    PATTERN ".svn" EXCLUDE)
