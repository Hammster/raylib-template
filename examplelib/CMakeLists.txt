file(GLOB_RECURSE _SOURCE RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.c)
file(GLOB_RECURSE _HEADER RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} *.h)

set(examplelib_public_headers
    lib.h
    )
add_library (examplelib lib.c ${_SOURCE} ${_HEADER})
