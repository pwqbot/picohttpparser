cmake_minimum_required(VERSION 3.6)
project(picohttpparser LANGUAGES C)

# Set the C standard
set(CMAKE_C_STANDARD 99)

# Build the library from picohttpparser.c
add_library(picohttpparser STATIC picohttpparser.c)
set_property(TARGET picohttpparser PROPERTY WINDOWS_EXPORT_ALL_SYMBOLS TRUE)

# Include the current directory to find picohttpparser.h
target_include_directories(picohttpparser PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

# Install the library and headers
include(GNUInstallDirs)
install(TARGETS picohttpparser
        ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR})
install (
    FILES picohttpparser.h
    DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
