### Core Definitions

cmake_minimum_required(VERSION 3.23)

set(PRIMARY_OUTPUT_NAME "cmakeProjectLayout")

set(CMAKE_CXX_STANDARD              17) # https://cmake.org/cmake/help/latest/variable/CMAKE_CXX_STANDARD.html
set(CMAKE_CXX_STANDARD_REQUIRED     ON) # https://cmake.org/cmake/help/latest/variable/CMAKE_CXX_STANDARD_REQUIRED.html
set(CMAKE_EXPORT_COMPILE_COMMANDS   ON) # https://cmake.org/cmake/help/latest/variable/CMAKE_EXPORT_COMPILE_COMMANDS.html
set(CMAKE_CXX_EXTENSIONS            OFF) # https://cmake.org/cmake/help/latest/variable/CMAKE_CXX_EXTENSIONS.html

project(${PRIMARY_OUTPUT_NAME} VERSION 1.0.0 LANGUAGES C CXX)

### Local Targets

set(PRIMARY_HEADER_FILES
    "inc/helloWorld.hh"
)

set(PRIMARY_SOURCE_FILES
    "src/helloWorld.cpp"
)

add_library(${PRIMARY_OUTPUT_NAME} STATIC
    ${PRIMARY_HEADER_FILES}
    ${PRIMARY_SOURCE_FILES}
)

target_include_directories(${PRIMARY_OUTPUT_NAME} PUBLIC
    "./inc"
)

target_link_libraries(${PRIMARY_OUTPUT_NAME} PRIVATE
    ${GREETER_MESSAGES_OUTPUT_NAME}
)
