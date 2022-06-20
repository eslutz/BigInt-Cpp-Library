# BigInt Library for C++

Code originally from [BigInt](https://github.com/faheel/BigInt).

This repo splits the header and class definitions into separate files and can be used to create a static library for use in other projects.

After downloading the source code, build the program to get the needed `libBigInt_Cpp.a` library file.  Take that file, and the header file and place them in folders as structured below.  Pick a location to keep the folder and then reference in the CMake file of any C++ project that needs to use the library.

#### Library Folder Structure
``` bash
.
|____BigIntCppLib
| |____include
| | |____BigInt.h
| |____lib
| | |____libBigInt_Cpp.a
```

#### CMake File Example To Link Library To A Project
``` cmake
cmake_minimum_required(VERSION 3.22)
project(ExampleProject)

set(CMAKE_CXX_STANDARD 23)
set(FIND_BIGINT_CPP_LIB_PATHS
        ~/Library/Frameworks/BigIntCppLib)

find_path(BIGINT_LIB_INCLUDE_DIR BigInt.h
        PATH_SUFFIXES include
        PATHS ${FIND_BIGINT_CPP_LIB_PATHS})

find_library(BIGINT_LIB
        NAMES BigInt_Cpp
        PATH_SUFFIXES lib
        PATHS ${FIND_BIGINT_CPP_LIB_PATHS})

add_executable(${PROJECT_NAME} main.cpp)

include_directories(${BIGINT_LIB_INCLUDE_DIR})

target_link_libraries(${PROJECT_NAME} ${BIGINT_LIB})
```