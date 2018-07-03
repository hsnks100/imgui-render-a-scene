cmake_minimum_required(VERSION 3.5)
project(imgui-opengl-glfw-glew-cmake-demo)

include(${CMAKE_ROOT}/Modules/ExternalProject.cmake)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_VERBOSE_MAKEFILE 1)
set(APP_VERSION_MAJOR 1)
set(APP_VERSION_MINOR 0) 
set(APP_TARGET imgui-demo.app)
set(SRC_FILES 
        imgui/imgui.cpp
        imgui/imgui.h
        imgui/imgui_demo.cpp
        imgui/imgui_draw.cpp
        imgui/examples/imgui_impl_glfw.cpp
        imgui/examples/imgui_impl_opengl3.cpp
        imgui/examples/libs/gl3w/GL/gl3w.c
        )
include_directories(${CMAKE_SOURCE_DIR}/imgui ${CMAKE_SOURCE_DIR}/imgui/examples ${CMAKE_SOURCE_DIR}/imgui/examples/libs/gl3w)

add_executable(${APP_TARGET} main.cpp ${SRC_FILES})
#add_dependencies(${APP_TARGET} imgui_external)
find_package(glfw3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
include_directories(${GLFW_INCLUDE_DIRS} ${OPENGL_INCLUDE_DIRS} ${GLEW_INCLUDE_DIRS})


target_link_libraries(
        ${APP_TARGET}
        glfw
        dl
        ${OPENGL_LIBRARIES}
        ${GLEW_LIBRARIES}
        ${EXTRA_LIBS}
        ${GLFW_LIBRARY_DIRS} 
)
