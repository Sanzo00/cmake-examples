cmake_minimum_required(VERSION 3.5)
project(compile_flags)

add_executable(${PROJECT_NAME}
  main.cpp
)

# Set a default C++ compile flag
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DEX2" CACHE STRING "Set C++ Compile Flags" FORCE)

target_compile_definitions(${PROJECT_NAME} PRIVATE EX3)