cmake_minimum_required(VERSION 3.5)
project(kalango_utils_lib C)

set(srcs .)

list(APPEND ${srcs} "print_out.c")    
list(APPEND ${srcs} "tlsf.c")    

add_library(${PROJECT_NAME} STATIC ${srcs})
set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)

target_include_directories(${PROJECT_NAME} PUBLIC  ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(${PROJECT_NAME} PRIVATE  printf)
target_include_directories(${PROJECT_NAME} PRIVATE  segger)
target_include_directories(${PROJECT_NAME} PRIVATE  segger/rtt)
target_include_directories(${PROJECT_NAME} PRIVATE  segger/systemview)    


