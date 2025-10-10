cmake_minimum_required( VERSION 3.31 )

project(imgui-master)
add_library( ${PROJECT_NAME} STATIC
    ${PROJECT_SOURCE_DIR}/imgui.cpp
    ${PROJECT_SOURCE_DIR}/imgui_demo.cpp
    ${PROJECT_SOURCE_DIR}/imgui_draw.cpp
    ${PROJECT_SOURCE_DIR}/imgui_widgets.cpp

    ${PROJECT_SOURCE_DIR}/backends/imgui_impl_glfw.cpp
    ${PROJECT_SOURCE_DIR}/backends/imgui_impl_vulkan.cpp
)

target_include_directories( ${PROJECT_NAME} PUBLIC
    ${PROJECT_SOURCE_DIR}/
    ${PROJECT_SOURCE_DIR}/backends/
)
