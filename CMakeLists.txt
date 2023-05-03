
cmake_minimum_required(VERSION 3.16.3)

project("generated_code")

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)

# Find requirements
find_package(fastcdr REQUIRED)
find_package(fastrtps REQUIRED)


message(STATUS "Configuring Helloworld...")
add_library(Helloworld_lib Helloworld.cxx)
target_link_libraries(Helloworld_lib fastcdr fastrtps)

add_executable(Helloworld HelloworldPubSubTypes.cxx HelloworldPublisher.cxx HelloworldSubscriber.cxx HelloworldPubSubMain.cxx)
target_link_libraries(Helloworld fastcdr fastrtps
        Helloworld_lib )



