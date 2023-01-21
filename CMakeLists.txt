cmake_minimum_required(VERSION 3.10...3.23)
project(dzgraph_suite)

set(CMAKE_CXX_STANDARD 20)

file(GLOB_RECURSE dzgraph_suite_SRC ${CMAKE_SOURCE_DIR}/src/*.cpp)
file(GLOB_RECURSE dzgraph_suite_INCLUDE ${CMAKE_SOURCE_DIR}/include/*.h ${CMAKE_SOURCE_DIR}/include/*.hpp)

add_executable(dzgraph_suite ${dzgraph_suite_SRC} ${dzgraph_suite_INCLUDE})

add_subdirectory(libs/glfw)
set(BUILD_SHARED_LIBS ON)
set(GLFW_BUILD_EXAMPLES OFF)
set(GLFW_BUILD_TESTS OFF)
set(GLFW_BUILD_DOCS OFF)
set(GLFW_INSTALL OFF)

target_include_directories(dzgraph_suite PRIVATE libs/glfw/include ${dzgraph_suite_INCLUDE})
target_link_libraries(dzgraph_suite PRIVATE glfw)
