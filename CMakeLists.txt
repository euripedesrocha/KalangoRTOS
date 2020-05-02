cmake_minimum_required(VERSION 3.5)
project(kalango_kernel_lib C)

add_subdirectory(ext)
add_subdirectory(utils)

file(GLOB arch_srcs "archs/*.c")
file(GLOB arch_srcs_a "archs/*.S")
file(GLOB kernel_srcs "src/*.c")

set(RTOS_SOURCES ${arch_srcs} ${arch_srcs_a} ${kernel_srcs})

add_library(${PROJECT_NAME}  STATIC ${RTOS_SOURCES})
set_target_properties(${PROJECT_NAME}  PROPERTIES LINKER_LANGUAGE C)

target_include_directories(${PROJECT_NAME} PUBLIC  include)
target_include_directories(${PROJECT_NAME} PUBLIC  external/printf)
target_include_directories(${PROJECT_NAME} PUBLIC  external/segger)
target_include_directories(${PROJECT_NAME} PUBLIC  external/segger/rtt)
target_include_directories(${PROJECT_NAME} PUBLIC  external/segger/systemview)
target_include_directories(${PROJECT_NAME} PRIVATE utils)


