cmake_minimum_required(VERSION 3.1)
project(bar)

set(CMAKE_CXX_STANDARD 11)

#set(CMAKE_SHARED_LINKER_FLAGS
#        ${CMAKE_SHARED_LINKER_FLAGS} -Wl,-rpath,'./:./lib:./3rdparty/foo/lib'
#        )

set(CMAKE_CXX_FLAGS
        ${CMAKE_CXX_FLAGS} -Wl,-rpath=./:./lib:./3rdparty/foo/lib
        )

add_library(bar SHARED bar.h bar.cc)

set_target_properties(bar
        PROPERTIES
        LINKER_LANGUAGE CXX
        ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
        LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib
        RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin
        OUTPUT_NAME bar
        )

target_include_directories(bar PRIVATE
        3rdparty/foo/include
        )

target_link_directories(bar PRIVATE
        3rdparty/foo/lib
        )

target_link_libraries(bar foo)