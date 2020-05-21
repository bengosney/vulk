cmake_minimum_required(VERSION 3.10)

set(BIN_NAME "Vulk")

project(${BIN_NAME} VERSION 0.1)

file(GLOB SOURCES "src/*.cpp")

include_directories("$ENV{VULKAN_SDK}/include")
link_directories("$ENV{VULKAN_SDK}/lib") 
link_directories("$ENV{VULKAN_SDK}/etc/explicit_layer.d")

find_package(glfw3 3.2 REQUIRED)

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -d -Wall")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -Wall")
set(CMAKE_CXX_STANDARD 11)

add_executable(${BIN_NAME} ${SOURCES})

target_link_libraries(${BIN_NAME} glfw)
target_link_libraries(${BIN_NAME} vulkan)

configure_file(version.h.in src/version.h)
configure_file(.gitignore.in .gitignore)