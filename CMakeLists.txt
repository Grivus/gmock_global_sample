cmake_minimum_required(VERSION 2.8)
project(gmock_global_sample)

set_property(GLOBAL PROPERTY USE_FOLDERS ON)
set_property(GLOBAL PROPERTY PREDEFINED_TARGETS_FOLDER "CMake")

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")

add_definitions( -DUNICODE -D_UNICODE )

add_subdirectory(googletest EXCLUDE_FROM_ALL)

set_target_properties(gmock PROPERTIES FOLDER GTest)
set_target_properties(gmock_main PROPERTIES FOLDER GTest)
set_target_properties(gtest PROPERTIES FOLDER GTest)
set_target_properties(gtest_main PROPERTIES FOLDER GTest)

include_directories(googletest/googletest/include)
include_directories(googletest/googlemock/include)
include_directories(gmock_global/include)

add_executable(gmock_global_sample main.cpp gmock_global/include/gmock_global/gmock_global.h)

target_link_libraries (gmock_global_sample gtest gmock)