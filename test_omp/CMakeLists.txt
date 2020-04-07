cmake_minimum_required(VERSION 3.15)
project(test_omp)

set(CMAKE_CXX_STANDARD 14)

find_package(PCL 1.7 REQUIRED)
find_package(OpenMP)
if (OPENMP_FOUND)
    set (CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${OpenMP_C_FLAGS}")
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()

include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
#add_definitions(${PCL_DEFINITIONS})


include_directories(include)
link_directories(lib)

add_executable(test_omp src/align.cpp )
target_link_libraries(test_omp
        ${PCL_LIBRARIES}
        ndt_omp
)