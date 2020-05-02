cmake_minimum_required(VERSION 3.5)
project(kalango_external_lib C)

set(srcs .)

add_compile_options(-includekalango_config.h)

file(GLOB printf_srcs "printf/*.c")
file(GLOB segger_rtt_srcs "segger/rtt/*.c")
file(GLOB segger_sysview_srcs "segger/systemview/*.c")
list(APPEND ${srcs} ${printf_srcs} ${segger_rtt_srcs} ${segger_sysview_srcs})    

add_library(${PROJECT_NAME} STATIC ${srcs})
set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE C)

target_include_directories(${PROJECT_NAME} PRIVATE  printf)
target_include_directories(${PROJECT_NAME} PRIVATE  segger)
target_include_directories(${PROJECT_NAME} PRIVATE  segger/rtt)
target_include_directories(${PROJECT_NAME} PRIVATE  segger/systemview)      


