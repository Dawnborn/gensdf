cmake_minimum_required(VERSION 3.1)
project(sdf_gen)

set(CMAKE_CXX_STANDARD 17) # to use to std::filesystem
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

# libigl
option(LIBIGL_WITH_OPENGL            "Use OpenGL"         ON)
option(LIBIGL_WITH_OPENGL_GLFW       "Use GLFW"           ON)
option(LIBIGL_WITH_CGAL              "Use CGAL"           ON)

# Libigl
include(libigl) # follow the example of https://github.com/libigl/libigl-example-project/tree/main
igl_include(core)
igl_include(glfw)
igl_include(copyleft cgal)
# find_package(LIBIGL REQUIRED QUIET)

# Add your project files
file(GLOB SRCFILES sdf_gen.cpp)
add_executable(${PROJECT_NAME} ${SRCFILES})
target_link_libraries(${PROJECT_NAME} igl::core igl::glfw igl_copyleft::cgal)
