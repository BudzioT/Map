cmake_minimum_required (VERSION 3.8)

project ("Map_Lighting")

add_executable (Map_Lighting "src/main.cpp" "include/glad-glad2/glad.h" "include/glad-glad2/glad.c" "include/stb_image.h" "src/Camera.h" "src/Shader.h" "src/stb_img.cpp")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

include(FetchContent)

FetchContent_Declare(
	glm
	GIT_REPOSITORY	https://github.com/g-truc/glm.git
	GIT_TAG 	bf71a834948186f4097caa076cd2663c69a10e1e #refs/tags/0.9.9.8
)

FetchContent_MakeAvailable(glm)

add_subdirectory(${CMAKE_SOURCE_DIR}/include/glfw-3.4)

target_link_libraries(Map_Lighting PRIVATE glfw glm::glm)

add_compile_definitions(TEXTURE_DIR="${CMAKE_SOURCE_DIR}/src/textures/"
	SHADER_DIR="${CMAKE_SOURCE_DIR}/src/shaders/")