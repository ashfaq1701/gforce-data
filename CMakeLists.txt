cmake_minimum_required(VERSION 3.27)
project(gforce_data)

set(CMAKE_CXX_STANDARD 17)

link_directories(libs/gforce/lib)

set(GFORCE_LIBRARY_PATH libs/gforce/lib)
add_library(gforce SHARED IMPORTED)

set_target_properties(gforce
        PROPERTIES
        IMPORTED_IMPLIB ${GFORCE_LIBRARY_PATH}/gforce64.lib)

add_executable(gforce_data main.cpp)
target_include_directories(gforce_data PRIVATE libs/gforce/inc)

target_link_libraries(gforce_data PRIVATE gforce)
