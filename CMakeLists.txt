cmake_minimum_required(VERSION 3.20)
project(ros2_simple_tests VERSION 0.0.1 DESCRIPTION "simple pub/sub/service tests for ros2")

set(CMAKE_CXX_STANDARD 17)
set(CXX_STANDARD_REQUIRED ON)

add_definitions(
    -Wall
    -Wcast-align
    -Wdisabled-optimization
    -Werror
    -Wextra
    -Wformat=2
    -Wfatal-errors
    -Wno-overloaded-virtual
    -Winit-self
    -Wmissing-include-dirs
    -Wreorder
    -Wsign-promo
    -Wswitch
    -Wunused
    -Wpedantic
    -Wno-unused-parameter # ros2 contains unused parameters
)

find_package(nav_msgs REQUIRED)
find_package(rcl REQUIRED)
find_package(rcl_logging_spdlog REQUIRED)
find_package(rclcpp_action REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rmw REQUIRED)
find_package(spdlog REQUIRED)
find_package(std_srvs REQUIRED)

#
# simple_server

add_executable(simple_server simple_server.cc)

target_link_libraries(simple_server PUBLIC
    ${nav_msgs_TARGETS}
    rcl::rcl
    rcl_logging_spdlog::rcl_logging_spdlog
    rclcpp_action::rclcpp_action
    rclcpp::rclcpp
    rmw::rmw
    ${std_srvs_TARGETS}
)

target_include_directories(simple_server PUBLIC
    ${nav_msgs_INCLUDE_DIRS}
    ${rcl_INCLUDE_DIRS}
    ${rcl_logging_spdlog_INCLUDE_DIRS}
    ${rclcpp_action_INCLUDE_DIRS}
    ${rclcpp_INCLUDE_DIRS}
    ${rmw_INCLUDE_DIRS}
    ${std_srvs_INCLUDE_DIRS}
)

#
# simple_publisher

add_executable(simple_publisher simple_publisher.cc)

target_link_libraries(simple_publisher PUBLIC
    ${nav_msgs_TARGETS}
    rcl::rcl
    rcl_logging_spdlog::rcl_logging_spdlog
    rclcpp_action::rclcpp_action
    rclcpp::rclcpp
    rmw::rmw
    ${std_srvs_TARGETS}
)

target_include_directories(simple_publisher PUBLIC
    ${nav_msgs_INCLUDE_DIRS}
    ${rcl_INCLUDE_DIRS}
    ${rcl_logging_spdlog_INCLUDE_DIRS}
    ${rclcpp_action_INCLUDE_DIRS}
    ${rclcpp_INCLUDE_DIRS}
    ${rmw_INCLUDE_DIRS}
    ${std_srvs_INCLUDE_DIRS}
)
