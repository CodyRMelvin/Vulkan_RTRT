cmake_minimum_required(VERSION 3.31)

set( CMAKE_CXX_COMPILER g++ )

project(CSRTRT LANGUAGES CXX)

add_subdirectory(src)
add_subdirectory(libs)

set_target_properties(${PROJECT_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/../bin/)

target_compile_definitions(${PROJECT_NAME} PRIVATE "$<$<CONFIG:Debug>:_DEBUG>")

set( CMAKE_CXX_STANDARD 17 )
target_compile_features( ${PROJECT_NAME} PUBLIC cxx_std_17 )

set( CMAKE_CXX_FLAGS "-Wall -Werror -Wextra" )
set( CMAKE_CXX_FLAGS_DEBUG "-g" )
set( CMAKE_CXX_FLAGS_RELEASE "-O4 -DNDEBUG" )

target_include_directories( ${PROJECT_NAME} PRIVATE libs )
target_link_libraries( ${PROJECT_NAME} PRIVATE libs )

add_custom_target(
    run
    COMMAND ${PROJECT_NAME}
    WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}"
    DEPENDS ${PROJECT_NAME}
)
