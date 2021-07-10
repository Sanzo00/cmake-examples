# set cmake minimum version
cmake_minimum_required(VERSION 3.5)

# set the project name
project(protobuf_exmaple)

# find the protobuf compiler and libraries
find_package(Protobuf REQUIRED)

# check if protobuf was found
if (PROTOBUF_FOUND)
  message("protobuf found")
else()
  message(FATAL_ERROR "Cannot find protobuf")
endif()

# generate the .h and .cxx files
PROTOBUF_GENERATE_CPP(PROTO_SRCS PROTO_HDRS AddressBook.proto)

# print path 
message("PROTO_SRCS = ${PROTO_SRCS}")
message("PROTO_HDRS = ${PROTO_HDRS}")

# add an executable
add_executable(${PROJECT_NAME} 
  main.cpp
  ${PROTO_SRCS}
  # ${PROTO_HDRS}  
)

target_include_directories(${PROJECT_NAME}
  PUBLIC
    ${PROTOBUF_INCLUDE_DIRS}
    ${CMAKE_CURRENT_BINARY_DIR}
)

target_link_libraries(${PROJECT_NAME}
  PUBLIC ${PROTOBUF_LIBRARIES}
)