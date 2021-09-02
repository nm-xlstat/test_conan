cmake_minimum_required(VERSION 3.20)


project(exe)
message( "start exe" )

set(
    SRCS
    main.cpp
    )


add_executable(caller ${SRCS} )
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT caller)
target_link_libraries(caller PRIVATE called)
