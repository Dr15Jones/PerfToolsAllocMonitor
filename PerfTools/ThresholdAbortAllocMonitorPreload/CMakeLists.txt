file(GLOB SOURCES src/*.cc)

add_library(PerfToolsThresholdAbortAllocMonitorPreload SHARED ${SOURCES})

target_sources(PerfToolsThresholdAbortAllocMonitorPreload
    PUBLIC
        FILE_SET HEADERS
        BASE_DIRS ${CMAKE_SOURCE_DIR}
)

target_link_libraries(PerfToolsThresholdAbortAllocMonitorPreload
  PUBLIC
  PerfToolsAllocMonitor
)

set_target_properties(PerfToolsThresholdAbortAllocMonitorPreload PROPERTIES
    VERSION 1.0.0
    SOVERSION 1
)
