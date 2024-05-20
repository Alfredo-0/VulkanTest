cmake_minimum_required(VERSION 3.10)

project(VulkanTest VERSION 1.0)

enable_testing()

set(CMAKE_CXX_STANDARD 17)
add_compile_options(-O2)

file(GLOB project_sources
 "src/*.cpp"
 )

add_executable(${PROJECT_NAME} ${project_sources})

find_package(Vulkan REQUIRED)

target_link_libraries(${PROJECT_NAME} PUBLIC
    /usr/lib/libglm.a
    /usr/lib/libglfw.so.3.4
    /usr/lib/libdecor/plugins-1/libdecor-gtk.so
    Vulkan::Vulkan
)

target_include_directories(${PROJECT_NAME} PUBLIC
    /usr/include/GLFW
    /usr/include/libdecor-0
    /usr/include/glm
)

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)