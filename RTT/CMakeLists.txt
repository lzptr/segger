project(segger_rtt)


file(GLOB PROJ_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/RTT/*.c")


add_library(${PROJECT_NAME} STATIC 
                ${CMAKE_CURRENT_SOURCE_DIR}/RTT/SEGGER_RTT.c
                ${CMAKE_CURRENT_SOURCE_DIR}/RTT/SEGGER_RTT_printf.c
                ${CMAKE_CURRENT_SOURCE_DIR}/Syscalls/SEGGER_RTT_Syscalls_GCC.c
)

target_include_directories(${PROJECT_NAME} PUBLIC 
  ${CMAKE_CURRENT_SOURCE_DIR}/RTT
  ${CMAKE_CURRENT_SOURCE_DIR}/Config
)