cmake_minimum_required(VERSION 3.0.2)
project(ros_tutorials_topic)
find_package(catkin REQUIRED COMPONENTS
  message_generation
  roscpp
  std_msgs
)

# declare message 
add_message_files(FILE MsgTotorial.msg)

# option for setting depending message
generate_message(DEPENDENCIES std_msgs)

# catkin_package option -> describe 
#     library
#     catkin build dependency
#     system dependent package
catkin_package(
  LIBRARY ros_tutorials_topic
  CATKIN_DEPENDS roscpp std_msgs
)

# generate include directory
include_directories(${catkin_INCLUDE_DIRS})

# topic_publisher node build option
add_executable(topic_publisher src/topic_publisher.cpp)
add_executable(topic_publisher ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(topic_publisher ${catkin_LIBRARIES})


# topic subscriber node build option
add_executable(topic_subcriber src/topic_subscriber.cpp)
add_executable(topic_subcriber ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(topic_subcriber ${catkin_LIBRARIES})
