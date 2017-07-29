cmake_minimum_required(VERSION 3.7)
project(cppbase)

#include headers and sources
include_directories(include /usr/local/include)

#compiler location
set(CMAKE_C_COMPILER  "/usr/bin/clang")
set(CMAKE_CXX_COMPILER  "/usr/bin/clang++")

#include c++17 standard
set(CMAKE_CXX_FLAGS "-std=c++1z -fPIC -g -Wall -pedantic")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

#use clang toolchain
set(CMAKE_LINKER_FLAGS "-stdlib=libc++ -lc++abi")

#include compilation database for youcompleteme
set(CMAKE_EXPORT_COMPILE_COMMANDS ON) 

#add queue benchmark
add_executable(cppbase_bench ../tests/queue_bench.cpp)
target_link_libraries(cppbase_bench pthread benchmark)


#add cppbase executable
add_executable(cppbase ../src/main.cpp)
target_link_libraries(cppbase pthread)




