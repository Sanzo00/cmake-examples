cmake_minimum_required(VERSION 3.5)
project(cmake_install)

############################################
# Create a library
############################################
add_library(cmake_inst SHARED
  src/Hello.cpp
)

target_include_directories(cmake_inst
  PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

############################################
# Create an executable
############################################
add_executable(cmake_install_bin
  src/main.cpp
)

target_link_libraries(cmake_install_bin 
  PRIVATE
    cmake_inst
)

############################################
# Install
############################################
# Binaries
install(TARGETS cmake_install_bin DESTINATION bin)

# Library
install(TARGETS cmake_inst LIBRARY DESTINATION lib)

# Header files
install(DIRECTORY ${PROJECT_SOURCE_DIR}/include/ DESTINATION include)

# Config
install(FILES cmake.conf DESTINATION etc)

# set make install directory
if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
  set(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/install" CACHE PATH "The path to use for make install" FORCE)
endif()

# Debug for CMAKE_INSTALL_PREFIX
message("CMAKE_INSTALL_PREFIX: " ${CMAKE_INSTALL_PREFIX})