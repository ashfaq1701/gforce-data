cmake_minimum_required(VERSION 3.27)
project(gforce_data)

set(CMAKE_CXX_STANDARD 17)

set(GFORCE_LIBRARY_PATH ${CMAKE_SOURCE_DIR}/libs/gforce/lib)
set(GEFORCE_INCLUDES_DIRECTORY ${CMAKE_SOURCE_DIR}/libs/gforce/inc)
add_library(gforce SHARED IMPORTED)

set_target_properties(gforce
        PROPERTIES
        IMPORTED_LOCATION ${GFORCE_LIBRARY_PATH}/gforce64.dll
        IMPORTED_IMPLIB ${GFORCE_LIBRARY_PATH}/gforce64.lib)

add_executable(gforce_data main.cpp)
target_include_directories(gforce_data PRIVATE ${GEFORCE_INCLUDES_DIRECTORY})

target_link_libraries(gforce_data PRIVATE gforce)

