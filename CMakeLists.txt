cmake_minimum_required(VERSION 3.20)

project(opencl)

# cuda
find_package(CUDA REQUIRED)
message("CUDA_OpenCL_LIBRARY:${CUDA_OpenCL_LIBRARY}")
include_directories(${CUDA_INCLUDE_DIRS})
if(CUDA_FOUND)
  message(STATUS "Found CUDA OpenCL libraries")
else()
  message(FATAL_ERROR "Not found CUDA libraries")
endif()

add_library(${PROJECT_NAME} INTERFACE IMPORTED GLOBAL)
target_include_directories(${PROJECT_NAME}
                           INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)
target_link_libraries(${PROJECT_NAME} INTERFACE ${CUDA_OpenCL_LIBRARY})
