cmake_minimum_required(VERSION 2.8)

project(SFMLApp) #Change this to your binary name of choice

file(GLOB_RECURSE SRC_CPP RELATIVE ${CMAKE_SOURCE_DIR} "src/*.cpp")
file(GLOB_RECURSE SRC_HPP RELATIVE ${CMAKE_SOURCE_DIR} "src/*.hpp")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -no-pie")

#file(COPY src/shaders src/images DESTINATION midia)

find_package(SFML 2.5 COMPONENTS window graphics audio system network REQUIRED)
#find_package(glm REQUIRED)

#INCLUDE(FindPackageHandleStandardArgs)
#INCLUDE(FindPkgConfig)
#INCLUDE(FindOpenGL REQUIRED)
#INCLUDE(FindGLEW REQUIRED)

#link_directories(LIBRARIES src/dependencies)

#INCLUDE_DIRECTORIES(${OPENGL_INCLUDE_DIR})
#INCLUDE_DIRECTORIES(${GLEW_INCLUDE_DIR})

add_executable(${PROJECT_NAME} ${SRC_HPP} ${SRC_CPP})

target_link_libraries(${PROJECT_NAME} sfml-window sfml-graphics sfml-audio sfml-system sfml-network)

install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin)
