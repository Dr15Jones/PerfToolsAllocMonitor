file(GLOB SOURCES src/*.cc)

add_library(PerfToolsPeriodicAllocMonitorPreload SHARED ${SOURCES})

target_sources(PerfToolsPeriodicAllocMonitorPreload
    PUBLIC
        FILE_SET HEADERS
        BASE_DIRS ${CMAKE_SOURCE_DIR}
)

target_link_libraries(PerfToolsPeriodicAllocMonitorPreload
  PUBLIC
  PerfToolsAllocMonitor
  Threads::Threads
)

set_target_properties(PerfToolsPeriodicAllocMonitorPreload PROPERTIES
    VERSION 1.0.0
    SOVERSION 1
)
