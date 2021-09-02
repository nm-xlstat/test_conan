cmake_minimum_required(VERSION 3.20)


project(test_lib)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(
    LIB_HEADERS
    framework.h
    )
        
    
set(
    LIB_SRCS
    dllmain.cpp
    )


add_library(called SHARED  ${LIB_HEADERS} ${LIB_SRCS} )
target_compile_definitions(called PRIVATE TEST_EXPORTS)
target_include_directories(called INTERFACE "${CMAKE_CURRENT_SOURCE_DIR}")


set(
    EXE_SRCS
    main.cpp
    )


add_executable(caller ${EXE_SRCS} )
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT caller)
target_link_libraries(caller PRIVATE called)

