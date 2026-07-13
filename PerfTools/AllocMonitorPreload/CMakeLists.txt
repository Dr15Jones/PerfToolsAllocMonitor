file(GLOB SOURCES src/*.cc)

add_library(PerfToolsAllocMonitorPreload SHARED ${SOURCES})

target_sources(PerfToolsAllocMonitorPreload
    PUBLIC
        FILE_SET HEADERS
        BASE_DIRS ${CMAKE_SOURCE_DIR}
)

target_link_libraries(PerfToolsAllocMonitorPreload
  PUBLIC
  PerfToolsAllocMonitor
)

set_target_properties(PerfToolsAllocMonitorPreload PROPERTIES
    VERSION 1.0.0
    SOVERSION 1
)
