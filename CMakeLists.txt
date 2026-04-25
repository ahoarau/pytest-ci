cmake_minimum_required(VERSION 3.22)
project(a)
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR})
find_package(Python REQUIRED COMPONENTS Interpreter)
find_package(Pytest REQUIRED)

