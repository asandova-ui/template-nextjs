
cmake_minimum_required(VERSION 3.29)
project(my_lib VERSION 0.1 LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 20)
add_library(my_lib src/lib.cpp)
target_include_directories(my_lib PUBLIC include)
enable_testing()
include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/refs/heads/main.zip
)
FetchContent_MakeAvailable(googletest)
add_executable(tests tests/test_add.cpp)
target_link_libraries(tests PRIVATE my_lib gtest_main)
add_test(NAME unit COMMAND tests)
