cmake_minimum_required(VERSION 3.0.2)
project(ab_tasks)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

find_package(Boost REQUIRED COMPONENTS system)
find_package(Eigen3 3.3.7 REQUIRED)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS
  abb_irb1300_moveit_config
  moveit_ros_planning_interface
  moveit_ros_move_group
  tf
  roscpp
  geometry_msgs
  std_msgs
  message_generation
  moveit_msgs
  actionlib
  actionlib_msgs
  ab_msgs
)

###################################
## catkin specific configuration ##
###################################
catkin_package(
   CATKIN_DEPENDS 
     abb_irb1300_moveit_config 
     roscpp
     tf
     message_runtime
     geometry_msgs
     moveit_msgs
     std_msgs
     actionlib_msgs
)

###########
## Build ##
###########

## Specify additional locations of header files
include_directories(
  ${catkin_INCLUDE_DIRS}
  include
)

## Declare a C++ executable
add_executable(ab_tasks src/main.cpp src/ab_interface.cpp src/utils.cpp)
# add_executable(service_sample_node src/service_sample_node.cpp)

## Add cmake target dependencies of the executable
add_dependencies(ab_tasks ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
# add_dependencies(service_sample_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

## Specify libraries to link a library or executable target against
target_link_libraries(ab_tasks
  ${catkin_LIBRARIES}
  Eigen3::Eigen
  jsoncpp
)
# target_link_libraries(service_sample_node
#   ${catkin_LIBRARIES}
# )
