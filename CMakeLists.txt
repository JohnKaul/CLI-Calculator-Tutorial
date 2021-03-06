cmake_minimum_required( VERSION 2.8 )

IF(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
        set( CMAKE_CXX_COMPILER "clang++" )
        find_library (LIBSTDCXX NAMES stdc++)
        add_compile_options(-stdlib=libstdc++)
ENDIF()

# Project name...
project( CLICalculator )

# ==---------------------------== #
# Product version...
# ==---------------------------== #

# set( PROJECT_VERSION 1.0 )
# ...or...
set( VERSION_MAJOR 0 )
set( VERSION_MINOR 4 )
set( VERSION_PATCH 0 )

# ==---------------------------== #
# Directory setup
# ==---------------------------== #
set( SRCS_DIR  ${CMAKE_CURRENT_SOURCE_DIR}/src )
set( SRCS_INCLUDE_DIR ${SRCS_DIR}/include )
set( DLL_SRCS_DIR ${SRCS_DIR}/lib )
set( EXTRA_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/../../include )

# EXECUTABLE_OUTPUT_PATH
# -----------------------
# set this variable to specify a common place where CMake should put all
# executable files (instead of CMAKE_CURRENT_BINARY_DIR)
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR})

# LIBRARY_OUTPUT_PATH
# -----------------------
# set this variable to specify a common place where CMake should put all
# libraries (instead of CMAKE_CURRENT_BINARY_DIR)
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR})

# ==---------------------------== #
# Misc.
# ==---------------------------== #

# enable warnings
add_definitions( -DWall )

# ==---------------------------== #
# Search directories
# ==---------------------------== #
include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_BINARY_DIR}
    ${EXECUTABLE_OUTPUT_PATH}
    ${LIBRARY_OUTPUT_PATH}
    ${SRCS_INCLUDE_DIR}
    ${DLL_SRCS_DIR}
    ${EXTRA_INCLUDE_DIR}
    )

# ==---------------------------== #
# Source file list.
# ==---------------------------== #
set ( REQ_LIBRARIES
        ${LIBSTDCXX}
        )
#---
# Executables
set( MAIN_SRCS
    ${SRCS_DIR}/main.cpp
    )

# ==---------------------------== #

# copy the LICENCE file to the build directory
configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/LICENSE
    ${EXECUTABLE_OUTPUT_PATH}/LICENSE @ONLY
    )

# copy the README file to the build directory
configure_file(
    ${CMAKE_CURRENT_SOURCE_DIR}/README.md
    ${EXECUTABLE_OUTPUT_PATH}/README.txt @ONLY
    )

add_executable( ${PROJECT_NAME} ${MAIN_SRCS} ) 

target_link_libraries( ${PROJECT_NAME}
    ${REQ_LIBRARIES}
    )

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${EXECUTABLE_OUTPUT_PATH}
    )

install(FILES
    ${EXECUTABLE_OUTPUT_PATH}/LICENSE
    DESTINATION ${EXECUTABLE_OUTPUT_PATH}
    )

install(FILES
    ${EXECUTABLE_OUTPUT_PATH}/README.txt
    DESTINATION doc
    )
