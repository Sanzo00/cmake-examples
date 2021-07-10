cmake_minimum_required(VERSION 3.5)
project(cf_example)

# set a project version
set(cf_example_VERSION_MAJOR 0)
set(cf_example_VERSION_MINOR 2)
set(cf_example_VERSION_PATCH 1)
set(cf_example_VERSION "${cf_example_VERSION_MAJOR}.${cf_example_VERSION_MINOR}.${cf_example_VERSION_PATCH}")

# call configure files on ver.h to set the version
# uses the standard ${VARIABLE} syntax in the file
configure_file(ver.h.in ${PROJECT_SOURCE_DIR}/ver.h)

# this file can only use the @VARIABLE syntax in the file
configure_file(path.h.in ${PROJECT_SOURCE_DIR}/path.h @ONLY)

add_executable(${PROJECT_NAME} main.cpp)

target_include_directories(${PROJECT_NAME}
  PRIVATE
    ${PROJECT_SOURCE_DIR}
)
