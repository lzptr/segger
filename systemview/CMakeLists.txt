project(segger_systemview)

add_library(${PROJECT_NAME} STATIC 
                ${CMAKE_CURRENT_SOURCE_DIR}/SEGGER/SEGGER_SYSVIEW.c
)

target_include_directories(${PROJECT_NAME} PUBLIC 
  ${CMAKE_CURRENT_SOURCE_DIR}/SEGGER
  ${CMAKE_CURRENT_SOURCE_DIR}/Config
)

target_link_libraries(${PROJECT_NAME} PUBLIC segger_rtt)