# CMake project file for OpenLibm

CMAKE_MINIMUM_REQUIRED(VERSION 2.8)

list(APPEND CMAKE_C_FLAGS "-fno-gnu89-inline -std=c99 -Wall -O3 -DASSEMBLER -D__BSD_VISIBLE -Wno-implicit-function-declaration")

set(OPENLIBM_HOME ${PROJECT_SOURCE_DIR})
include("CMake/ConfigFlags.cmake")

set(SUBDIRS src ld80 ${ARCH} bsdsrc)
list(APPEND INCLUDES include ${CMAKE_CURRENT_SOURCE_DIR})

foreach(SUBD ${SUBDIRS})
    add_subdirectory(${SUBD})
    list(APPEND INCLUDES "${SUBD}")
    list(APPEND SRCS "${CUR_SRCS}")
endforeach()

message("${INCLUDE_DIRECTORIES}")

include_directories(${INCLUDES})
add_library(openlibm SHARED ${SRCS})

target_link_libraries(openlibm openlibm)
