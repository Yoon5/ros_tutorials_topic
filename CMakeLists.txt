cmake_minimum_required(VERSION 2.8.3)
project(ros_tutorials_topic)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  message_generation
  roscpp
  std_msgs
)

################################################
## Declare ROS messages, services and actions ##
################################################

add_message_files(
  FILES
  MsgTutorial.msg
)

generate_messages(DEPENDENCIES std_msgs)

###################################
## catkin specific configuration ##
###################################
catkin_package(
LIBRARIES ros_tutorial_topic
CATKIN_DEPENDS roscpp std_msgs
)

###########
## Build ##
###########

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(topic_publisher src/topic_publisher.cpp)
add_dependencies(topic_publisher ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(topic_publisher ${catkin_LIBRARIES})

add_executable(topic_subscriber src/topic_subscriber.cpp)
add_dependencies(topic_subscriber ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(topic_subscriber ${catkin_LIBRARIES})



