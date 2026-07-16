cmake_minimum_required(VERSION 3.23...4.0)

project(PerfTools VERSION 1.0.0 LANGUAGES CXX)

# Set default build type if not specified
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  set(CMAKE_BUILD_TYPE "Release" CACHE STRING "Build type" FORCE)
endif()

# Set C++ standard (C++20 required for concepts)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Set output directories
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

# Include GNUInstallDirs early so variables are available for environment scripts
include(GNUInstallDirs)

#handle threading
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

# Add compile options
add_compile_options(-Wall -Werror=return-type -Wno-attributes)
add_link_options(LINKER:-z,defs)

# Add subdirectories
add_subdirectory(PerfTools)

# ============================================================================
# Installation and package configuration
# ============================================================================

include(CMakePackageConfigHelpers)

# Set installation directories
set(LIB_INSTALL_DIR ${CMAKE_INSTALL_LIBDIR})

# Install all targets with EXPORT
# Note: This assumes all libraries are built as SHARED libraries
# and should be exported together

# Get all library targets that were created
set(PerfTools_EXPORT_TARGETS
  PerfToolsAllocMonitorPreload
  PerfToolsMaxMemoryPreload
  PerfToolsAllocMonitor
)

# Install libraries and executables
foreach(target ${PerfTools_EXPORT_TARGETS})
    if(TARGET ${target})
        install(TARGETS ${target}
            EXPORT StitchedTargets
            LIBRARY DESTINATION ${LIB_INSTALL_DIR}
            ARCHIVE DESTINATION ${LIB_INSTALL_DIR}
            RUNTIME DESTINATION ${BIN_INSTALL_DIR}
            FILE_SET HEADERS
        )
    endif()
endforeach()


# Print installation information
message(STATUS "PerfTools will be installed to: ${CMAKE_INSTALL_PREFIX}")
message(STATUS "  Libraries: ${CMAKE_INSTALL_PREFIX}/${LIB_INSTALL_DIR}")
