file(GLOB_RECURSE _SOURCE RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.c)
file(GLOB_RECURSE _HEADER RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.h)

if(MSVC)
  add_executable(example WIN32 main.c ${_SOURCE} ${_HEADER})
else()
  add_executable(example main.c ${_SOURCE} ${_HEADER})
endif()

include_directories(raylib_public_headers)
include_directories(../examplelib)

target_include_directories(example PUBLIC _SOURCE _HEADER)
target_link_libraries(example PRIVATE raylib)
target_link_libraries(example PUBLIC examplelib)

# copy SDL2
# if(MSVC)
#   message("### Copy DLLs (Windows Only)")
#   add_custom_command(TARGET example POST_BUILD		# Adds a post-build event to MyTest
#     COMMAND ${CMAKE_COMMAND} -E copy_if_different	# which executes "cmake - E copy_if_different..."
#       "${SDL2_BINARY_DIR}/${CMAKE_BUILD_TYPE}/sdl2d.dll"			# <--this is in-file
#       "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_BUILD_TYPE}/")			# <--this is out-file path
# endif()