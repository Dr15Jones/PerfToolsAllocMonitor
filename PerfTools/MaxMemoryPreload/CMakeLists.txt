file(GLOB SOURCES src/*.cc)

add_library(PerfToolsMaxMemoryPreload SHARED ${SOURCES})

target_sources(PerfToolsMaxMemoryPreload
    PUBLIC
        FILE_SET HEADERS
        BASE_DIRS ${CMAKE_SOURCE_DIR}
)

target_link_libraries(PerfToolsMaxMemoryPreload
  PUBLIC
  PerfToolsAllocMonitor
)

set_target_properties(PerfToolsMaxMemoryPreload PROPERTIES
    VERSION 1.0.0
    SOVERSION 1
)
