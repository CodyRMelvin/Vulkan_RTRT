cmake_minimum_required( VERSION 3.31 )

project(libs)

add_library( ${PROJECT_NAME} INTERFACE )

add_subdirectory(glm)
add_subdirectory(imgui-master)

find_package( glm REQUIRED )
find_package( glfw3 REQUIRED )
find_package( assimp REQUIRED )
find_package( Vulkan REQUIRED )

target_link_libraries( ${PROJECT_NAME} INTERFACE glfw )
target_link_libraries( ${PROJECT_NAME} INTERFACE glm::glm )
target_link_libraries( ${PROJECT_NAME} INTERFACE Vulkan::Vulkan )
target_link_libraries( ${PROJECT_NAME} INTERFACE assimp )
target_link_libraries( ${PROJECT_NAME} INTERFACE imgui-master )

include_directories(glm)
include_directories(glfw/include)
include_directories(assimp/include)
include_directories(imgui-master)
