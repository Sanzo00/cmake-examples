# set project name
project(subbinary)

# create the executable
add_executable(${PROJECT_NAME} main.cpp)

# link the static library from sublibrary1 using it's alias sub::lib1
# link the header only library from sublibrary2 using it's alias sub::lib2
# this will cause the include directories for that target to be added to this project
target_link_libraries(${PROJECT_NAME}
  sub::lib1
  sub::lib2
)

message("CMAKE_SOURCE_DIR: ${CMAKE_SOURCE_DIR}")
message("CMAKE_CURRENT_SOURCE_DIR: ${CMAKE_CURRENT_SOURCE_DIR}")
message("PROJECT_SOURCE_DIR: ${PROJECT_SOURCE_DIR}")
message("CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}")
message("CMAKE_CURRENT_BINARY_DIR: ${CMAKE_CURRENT_BINARY_DIR}")
message("PROJECT_BINARY_DIR: ${PROJECT_BINARY_DIR}")
