cmake_minimum_required(VERSION 2.8)

# See: https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html
SET(CMAKE_CXX_FLAGS "-Ofast")

add_library(gason STATIC
	src/gason.cpp
)

set_target_properties(gason PROPERTIES COMPILE_OPTIONS -ffunction-sections)
set_target_properties(gason PROPERTIES LINK_FLAGS "-Wl,-gc-sections")

install(TARGETS gason
    DESTINATION "lib"
)

install(FILES 
	src/gason.hpp 
	src/jsonbuilder.hpp
    DESTINATION "include/gason"
)