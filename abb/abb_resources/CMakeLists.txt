cmake_minimum_required(VERSION 3.0.2)
project(abb_resources)

find_package(catkin REQUIRED)

catkin_package()

install(DIRECTORY urdf
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
install(FILES LICENSE
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
