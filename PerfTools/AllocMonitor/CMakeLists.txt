# FWCore/Framework library
file(GLOB SOURCES src/*.cc)
file(GLOB HEADERS interface/*.h)

add_library(PerfToolsAllocMonitor SHARED ${SOURCES})

target_include_directories(PerfToolsAllocMonitor
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}>
        $<INSTALL_INTERFACE:include>
)

target_sources(PerfToolsAllocMonitor
    PUBLIC
        FILE_SET HEADERS
        BASE_DIRS ${CMAKE_SOURCE_DIR}
        FILES ${HEADERS}
)

target_link_libraries(PerfToolsAllocMonitor
  PUBLIC
  dl
)

set_target_properties(PerfToolsAllocMonitor PROPERTIES
    VERSION 1.0.0
    SOVERSION 1
)
