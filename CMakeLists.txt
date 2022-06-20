cmake_minimum_required(VERSION 3.22)
project(BigInt_Cpp)

set(CMAKE_CXX_STANDARD 23)

add_library(${PROJECT_NAME} BigInt.cpp)
