cmake_minimum_required(VERSION 2.8.3)
project(coxslam)

add_definitions(-std=c++14 -Werror)

find_package(catkin_simple REQUIRED)
catkin_simple(ALL_DEPS_REQUIRED)

cs_add_library(${PROJECT_NAME}
  src/client/coxslam_client.cpp
  src/server/coxslam_server.cpp
)

cs_add_executable(coxslam_client_node
  src/coxslam_client_node.cpp
)
target_link_libraries(coxslam_client_node ${PROJECT_NAME})

cs_add_executable(coxslam_server_node
    src/coxslam_server_node.cpp)
target_link_libraries(coxslam_server_node ${PROJECT_NAME})

cs_export()