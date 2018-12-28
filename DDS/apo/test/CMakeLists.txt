
cmake_minimum_required(VERSION 2.8.12)

project("generated_code")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)

# Find requirements
find_package(fastcdr REQUIRED)
find_package(fastrtps REQUIRED)


message(STATUS "Configuring Hello...")
add_library(Hello_lib Hello.cxx)
target_link_libraries(Hello_lib fastcdr fastrtps)

add_executable(Hello HelloPubSubTypes.cxx HelloPublisher.cxx HelloSubscriber.cxx HelloPubSubMain.cxx)
target_link_libraries(Hello fastcdr fastrtps
        Hello_lib )

