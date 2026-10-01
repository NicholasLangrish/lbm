cmake_minimum_required(VERSION 3.16)
project(lbm LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)   # lets VS Code understand your code

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_FLAGS_DEBUG   "-O0 -g -fsanitize=address,undefined -fno-omit-frame-pointer")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -march=native -DNDEBUG")

find_package(OpenMP REQUIRED)

add_executable(lbm src/main.cpp)
target_compile_options(lbm PRIVATE -Wall -Wextra -Wpedantic)
target_link_libraries(lbm PRIVATE OpenMP::OpenMP_CXX)