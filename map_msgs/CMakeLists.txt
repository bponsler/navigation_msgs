cmake_minimum_required(VERSION 2.8.3)
project(map_msgs)

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(rosidl_default_runtime REQUIRED)

rosidl_generate_interfaces(${PROJECT_NAME}
  "msg/OccupancyGridUpdate.msg"
  "msg/PointCloud2Update.msg"
  "msg/ProjectedMapInfo.msg"
  "msg/ProjectedMap.msg"
  "srv/GetMapROI.srv"
  "srv/GetPointMapROI.srv"
  "srv/GetPointMap.srv"
  "srv/ProjectedMapsInfo.srv"
  "srv/SaveMap.srv"
  "srv/SetMapProjections.srv"
  DEPENDENCIES builtin_interfaces std_msgs sensor_msgs nav_msgs)

set(INCLUDE_DIRS ${ament_cmake_INCLUDE_DIRS} ${std_msgs_INCLUDE_DIRS}
  ${sensor_msgs_INCLUDE_DIRS} ${nav_msgs_INCLUDE_DIRS}
  ${builtin_interfaces_INCLUDE_DIRS} ${rosidl_default_generators_INCLUDE_DIRS}
  ${rosidl_default_runtime_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS} ${std_msgs_LIBRARY_DIRS}
  ${sensor_msgs_LIBRARY_DIRS} ${nav_msgs_LIBRARY_DIRS}
  ${builtin_interfaces_LIBRARY_DIRS} ${rosidl_default_generators_LIBRARY_DIRS}
  ${rosidl_default_runtime_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES} ${std_msgs_LIBRARIES} ${sensor_msgs_LIBRARIES}
  ${nav_msgs_LIBRARIES} ${builtin_interfaces_LIBRARIES}
  ${rosidl_default_generators_LIBRARIES} ${rosidl_default_runtime_LIBRARIES})

ament_export_dependencies(ament_cmake)
ament_export_dependencies(std_msgs)
ament_export_dependencies(sensor_msgs)
ament_export_dependencies(nav_msgs)
ament_export_dependencies(builtin_interfaces)
ament_export_dependencies(rosidl_default_generators)
ament_export_dependencies(rosidl_default_runtime)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
