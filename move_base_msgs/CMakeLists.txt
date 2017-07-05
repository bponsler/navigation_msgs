cmake_minimum_required(VERSION 3.5)
project(move_base_msgs)

find_package(ament_cmake REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(actionlib_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(rosidl_default_runtime REQUIRED)

set(INCLUDE_DIRS ${ament_cmake_INCLUDE_DIRS} ${builtin_interfaces_INCLUDE_DIRS}
  ${actionlib_msgs_INCLUDE_DIRS} ${geometry_msgs_INCLUDE_DIRS}
  ${rosidl_default_generators_INCLUDE_DIRS} ${rosidl_default_runtime_INCLUDE_DIRS})
include_directories(${INCLUDE_DIRS})

set(LIBRARY_DIRS ${ament_cmake_LIBRARY_DIRS} ${builtin_interfaces_LIBRARY_DIRS}
  ${actionlib_msgs_LIBRARY_DIRS} ${geometry_msgs_LIBRARY_DIRS}
  ${rosidl_default_generators_LIBRARY_DIRS} ${rosidl_default_runtime_LIBRARY_DIRS})

link_directories(${LIBRARY_DIRS})

set(LIBS ${ament_cmake_LIBRARIES} ${builtin_interfaces_LIBRARIES}
  ${actionlib_msgs_LIBRARIES} ${geometry_msgs_LIBRARIES}
  ${rosidl_default_generators_LIBRARIES} ${rosidl_default_runtime_LIBRARIES})

add_action_files(DIRECTORY action FILES MoveBase.action)

ament_export_dependencies(ament_cmake)
ament_export_dependencies(builtin_interfaces)
ament_export_dependencies(actionlib_msgs)
ament_export_dependencies(geometry_msgs)
ament_export_dependencies(rosidl_default_generators)
ament_export_dependencies(rosidl_default_runtime)
ament_export_include_directories(${INCLUDE_DIRS})

ament_package()
