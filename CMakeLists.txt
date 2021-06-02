# Works with 3.11 and tested through 3.15
cmake_minimum_required(VERSION 3.14)

# Project name and a few useful settings. Other commands can pick up the results
project(RaylibTemplate
	VERSION 0.0.1
	DESCRIPTION "Raylib Template"
	LANGUAGES C)

# Only do these if this is the main project, and not if it is included through add_subdirectory
if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
	set(C_STANDARD  99)
	set(CMAKE_C_STANDARD_REQUIRED TRUE)

	# if(NOT CMAKE_C_FLAGS_DEBUG)
	# 	set(CMAKE_BUILD_TYPE Debug)
	# else()
	# 	set(CMAKE_BUILD_TYPE Release)
	# endif()

	message("######## ---- ${CMAKE_BUILD_TYPE} ---- #########")

	# Let's nicely support folders in IDE's
	set_property(GLOBAL PROPERTY USE_FOLDERS ON)
endif()

# FetchContent added in CMake 3.11, downloads during the configure step
include(FetchContent)

message("### Fetch Libraries")

# Raylib library
FetchContent_Declare(
	raylib
	GIT_REPOSITORY	https://github.com/raysan5/raylib.git
	GIT_TAG					3.7.0
	)

message("### Make Libraries Available")
# Adds Raylib
FetchContent_MakeAvailable(raylib)

message("### Build app")
add_subdirectory (example)
add_subdirectory (examplelib)
