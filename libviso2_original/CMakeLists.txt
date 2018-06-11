cmake_minimum_required(VERSION 2.8.3)
project(libviso2_original)

find_package(catkin REQUIRED )

#set(CMAKE_CXX_FLAGS "-msse3")
add_definitions(-msse3)

catkin_package(
  INCLUDE_DIRS libviso2/src
  LIBRARIES libviso2_original
)

include_directories(libviso2/src
  ${catkin_INCLUDE_DIRS}
)

add_library(libviso2_original
  libviso2/src/filter.cpp
  libviso2/src/matcher.cpp
  libviso2/src/matrix.cpp
  libviso2/src/reconstruction.cpp
  libviso2/src/triangle.cpp
  libviso2/src/viso.cpp
  libviso2/src/viso_stereo.cpp)

install(TARGETS libviso2_original
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY ${PROJECT_NAME}/src
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  PATTERN ".cpp" EXCLUDE
)

