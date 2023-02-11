cmake_minimum_required(VERSION 3.16)

project(Object-Viewer)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Werror -std=c++17 -DIMGUI_IMPL_OPENGL_LOADER_GLEW")
set(source_dir "${PROJECT_SOURCE_DIR}/src/")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

find_package(glfw3 3.3 REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)

include_directories(src/deps/imgui)

file(GLOB source_files "${source_dir}/*.cpp" "${source_dir}/deps/*.cpp" "${source_dir}/deps/*/*.cpp" "${source_dir}/deps/imgui/backends/imgui_impl_glfw.cpp" "${source_dir}/deps/imgui/backends/imgui_impl_opengl3.cpp" )

add_executable (viewer ${source_files})
target_link_libraries(viewer glfw)
target_link_libraries(viewer OpenGL::GL)
target_link_libraries(viewer GLEW::GLEW)
