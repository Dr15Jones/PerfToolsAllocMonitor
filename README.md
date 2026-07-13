# PerfToolsAllocMonitor

## Introduction
The PerfToolsAllocMonitor system is used to monitor the memory allocation/deallocation of C and C++ applications. This was developed for use in the CMS Experiment's data processing system but is sufficienly generic to use outside of that ecosystem.

The core code of the system is in PerfTools/AllocMonitorPreload which includes a more extensive README.md. The description of how to extend the monitoring can be found in PerfTools/AllocMonitor and its associated README.md file.

## Using the system

One can get a simple measurement of an applications memory use by doing
```
LD_PRELOAD="libPerfToolsMaxMemoryPreload.so libPerfToolsAllocMonitorPreload.so" applicationToMonitor
```

A full explanation can be found in PerfTools/MaxMemoryPreload/README.md

## Building the code
The code uses a standard CMake build system and has no dependencies outside of a C++ compiler and Linux's dynamic loading library, libdl.

```
> git clone https://github.com/Dr15Jones/PerfToolsAllocMonitor.git
> mkdir build
> cd build
> cmake ../PerfToolsAllocMonitor
> make
```
