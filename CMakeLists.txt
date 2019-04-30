set(PROJECT "FloydWarshall")
project(${PROJECT} CXX)

cmake_minimum_required(VERSION 3.5)

include(CheckCXXCompilerFlag)

CHECK_CXX_COMPILER_FLAG("-std=c++14" COMPILER_SUPPORTS_CXX14)
if (COMPILER_SUPPORTS_CXX14)
    add_compile_options("-std=c++14")
else()
    message(FATAL_ERROR "Compiler ${CMAKE_CXX_COMPILER} has no C++14 support.")
endif()

# ------------------------------------------------------------------------------

add_compile_options("-O3")

include_directories(${PROJECT_SOURCE_DIR}/include)
file(GLOB_RECURSE SRCS ${PROJECT_SOURCE_DIR}/src/*.cpp)

add_executable(floydwarshall ${PROJECT_SOURCE_DIR}/main.cpp ${SRCS})