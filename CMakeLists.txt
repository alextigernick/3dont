cmake_minimum_required (VERSION 3.0)
project (3dont)
cmake_policy(SET CMP0072 NEW)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED STATIC)

add_subdirectory(dep/glfw)

include_directories(dep/glfw/include)
include_directories(${GLEW_INCLUDE_DIRS})
FIND_FILE(TestLib libGLEW.so.2.1 /usr/lib64/)
set(ALL_LIBS
	${OPENGL_LIBRARY}
    ${GLFW_LIBRARIES}
    ${GLEW_LIBRARIES}
    glfw
    ${TestLib}
)

include_directories(
	dep/glfw/include/
	dep/glm/
	dep/glew/include/
	.
)
add_executable(main 
	src/main.cpp
)
target_link_libraries(main
	${ALL_LIBS}
)
set_target_properties(main PROPERTIES
            CXX_STANDARD 17)