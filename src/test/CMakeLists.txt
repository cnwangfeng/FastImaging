cmake_minimum_required(VERSION 2.8.9)

project(Testing_libstp)

add_library(libstp ${CMAKE_CURRENT_SOURCE_DIR}/../libstp/convolution/conv_func.cpp ${CMAKE_CURRENT_SOURCE_DIR}/../libstp/gridder/gridder.cpp)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/../../build/bin/test/)

find_package(GTest REQUIRED)
include_directories(${GTEST_INCLUDE_DIRS})
target_link_libraries(libstp ${GTEST_LIBRARIES} pthread)

# Convolution Functions Tests

# Triangle
add_executable(test_conv_triangle_func conv_func/conv_func_triangle.cpp)
target_link_libraries(test_conv_triangle_func gtest gtest_main libstp)

# Tophat
add_executable(test_conv_tophat conv_func/conv_func_tophat.cpp)
target_link_libraries(test_conv_tophat gtest gtest_main libstp)

# Sinc
add_executable(test_conv_sinc conv_func/conv_func_sinc.cpp)
target_link_libraries(test_conv_sinc gtest gtest_main libstp)

# Gaussian
add_executable(test_conv_gaussian conv_func/conv_func_gaussian.cpp)
target_link_libraries(test_conv_gaussian gtest gtest_main libstp)

# Gaussian Sinc
add_executable(test_conv_gaussian_sinc conv_func/conv_func_gaussiansinc.cpp)
target_link_libraries(test_conv_gaussian_sinc gtest gtest_main libstp)


# Kernel Functions Tests

# Oversampled Pillbox
add_executable(test_kernel_generation_oversampled_pillbox kernel_func/kernel_func_OversampledPillbox.cpp)
target_link_libraries(test_kernel_generation_oversampled_pillbox gtest gtest_main libstp)

# Oversampled Pillbox Small
add_executable(test_kernel_generation_oversample_pillbox_small kernel_func/kernel_func_OversampledPillboxSmall.cpp)
target_link_libraries(test_kernel_generation_oversample_pillbox_small gtest gtest_main libstp)

# Regular Sampling Pillbox
add_executable(test_kernel_generation_regular_sampling_pillbox kernel_func/kernel_func_RegularSamplingPillbox.cpp)
target_link_libraries(test_kernel_generation_regular_sampling_pillbox gtest gtest_main libstp)

# Regular Sampling Triangle
add_executable(test_kernel_generation_regular_sampling_triangle kernel_func/kernel_func_RegularSamplingTriangle.cpp)
target_link_libraries(test_kernel_generation_regular_sampling_triangle gtest gtest_main libstp)


#Gridder Functions Tests

# Single Pixel Overlap Pillbox
add_executable(test_gridder_bouns_checking gridder_func/gridder_func_BoundsChecking.cpp)
target_link_libraries(test_gridder_bouns_checking gtest gtest_main libstp)

# Single Pixel Overlap Pillbox
add_executable(test_gridder_multi_pixel_pillbox gridder_func/gridder_func_MultiPixelPillbox.cpp)
target_link_libraries(test_gridder_multi_pixel_pillbox gtest gtest_main libstp)

# Single Pixel Overlap Pillbox
add_executable(test_gridder_multiple_complex_vis gridder_func/gridder_func_MultipleComplexVis.cpp)
target_link_libraries(test_gridder_multiple_complex_vis gtest gtest_main libstp)

# Single Pixel Overlap Pillbox
add_executable(test_gridder_nearby_complex_vis gridder_func/gridder_func_NearbyComplexVis.cpp)
target_link_libraries(test_gridder_nearby_complex_vis gtest gtest_main libstp)

# Single Pixel Overlap Pillbox
add_executable(test_gridder_single_pixel_overlap_pillbox gridder_func/gridder_func_SinglePixelOverlapPillbox.cpp)
target_link_libraries(test_gridder_single_pixel_overlap_pillbox gtest gtest_main libstp)

# Single Pixel Overlap Pillbox
add_executable(test_gridder_small_pillbox gridder_func/gridder_func_SmallPillbox.cpp)
target_link_libraries(test_gridder_small_pillbox gtest gtest_main libstp)
