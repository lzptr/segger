project(segger_systemview)

if (NOT DEFINED SEGGER_SYSVIEW_TIMESTAMP_BITS)
  message("Using 32bit default size for the SystemTick timestamp")
else()
  message("Using ${SEGGER_SYSVIEW_TIMESTAMP_BITS} bit size for the SystemTick timestamp")
endif()

add_library(${PROJECT_NAME} STATIC 
                ${CMAKE_CURRENT_SOURCE_DIR}/SEGGER/SEGGER_SYSVIEW.c
)

target_include_directories(${PROJECT_NAME} PUBLIC 
  ${CMAKE_CURRENT_SOURCE_DIR}/SEGGER
  ${CMAKE_CURRENT_SOURCE_DIR}/Config
)

if (SEGGER_SYSVIEW_TIMESTAMP_BITS)
  target_compile_options(${PROJECT_NAME} PRIVATE -DSEGGER_SYSVIEW_TIMESTAMP_BITS=${SEGGER_SYSVIEW_TIMESTAMP_BITS})
endif()

target_link_libraries(${PROJECT_NAME} PUBLIC segger_rtt)