cmake_minimum_required(VERSION 3.5)
project(third_party_library)

# find a boost install with the libraries filesystem and system
find_package(Boost 1.46.1 REQUIRED COMPONENTS filesystem system)

# check if boost was found
if(Boost_FOUND)
  message("boost found")
else()
  message(FATAL_ERROR "Cannot find boost")
endif()


add_executable(${PROJECT_NAME}
  main.cpp
)

# link against the boost libraries
target_link_libraries(${PROJECT_NAME}
  PRIVATE
    Boost::filesystem
)