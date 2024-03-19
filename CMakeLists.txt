cmake_minimum_required(VERSION 3.27)
project(gforce_data)

set(CMAKE_CXX_STANDARD 14)
add_definitions(-D_UNICODE -DUNICODE)

set(GFORCE_BIN_PATH ${CMAKE_SOURCE_DIR}/dependencies/bin/)
set(GFORCE_LIB_PATH ${CMAKE_SOURCE_DIR}/dependencies/lib/)
set(GEFORCE_INCLUDES_DIRECTORY ${CMAKE_SOURCE_DIR}/inc)
set(SRC_DIRECTORY ${CMAKE_SOURCE_DIR}/src)

add_library(gforce SHARED IMPORTED)
set_target_properties(gforce PROPERTIES IMPORTED_LOCATION ${GFORCE_BIN_PATH}/gforce64.dll)
set_target_properties(gforce PROPERTIES IMPORTED_IMPLIB ${GFORCE_LIB_PATH}/gforce64.lib)

add_executable(gforce_data src/SerialDetect.cpp src/stdafx.cpp main.cpp)

target_include_directories(gforce_data PRIVATE ${GEFORCE_INCLUDES_DIRECTORY})
target_include_directories(gforce_data PRIVATE ${SRC_DIRECTORY})

target_link_libraries(gforce_data PRIVATE gforce)

