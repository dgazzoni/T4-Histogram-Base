cmake_minimum_required(VERSION 3.10)

project(histogram
    LANGUAGES C CXX CUDA)

find_package(CUDA REQUIRED)

add_executable(serial   src/histogram-serial.c)
add_executable(parallel src/histogram-parallel.cu)

target_link_libraries(serial m)
target_link_libraries(parallel m)

set_property(
    TARGET   parallel
    PROPERTY CUDA_ARCHITECTURES OFF)
