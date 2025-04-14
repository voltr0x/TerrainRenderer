cmake_minimum_required(VERSION 3.10)
project(TerrainRenderer)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Include GLFW from source
add_subdirectory(external/glfw)

# GLAD - assuming you will manually add glad.c and glad.h later
add_library(glad src/glad.c)
target_include_directories(glad PUBLIC include)

# Include GLM (header-only, just put the folder in external/)
include_directories(external/glm)

# Include directories
include_directories(include)
include_directories(external/glfw/include)

# Gather all .cpp files
file(GLOB_RECURSE SOURCES "src/*.cpp")

# Executable
add_executable(${PROJECT_NAME} ${SOURCES})

# Link everything
target_link_libraries(${PROJECT_NAME} glfw glad opengl32)