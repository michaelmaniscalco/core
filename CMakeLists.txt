cmake_minimum_required(VERSION 3.5.1)

set(CMAKE_INSTALL_PREFIX /usr/local)
project(core)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BUILD_TYPE Release)

add_compile_options(
    -O3
    -march=native
    -pipe
)

include_directories(./src)
file(GLOB_RECURSE SOURCES ./src/include/*.h)

add_library(HEADER_ONLY_TARGET STATIC ${SOURCES})
set_target_properties(HEADER_ONLY_TARGET PROPERTIES LINKER_LANGUAGE CXX)

install(TARGETS
    LIBRARY DESTINATION ${CMAKE_INSTALL_PREFIX}/lib/
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_PREFIX}/include/maniscalco/)
