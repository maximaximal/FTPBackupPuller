project(FTPBackupPuller)
cmake_minimum_required(VERSION 2.8.11)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

set(HDR ${CMAKE_CURRENT_SOURCE_DIR}/include)
set(SRC ${CMAKE_CURRENT_SOURCE_DIR}/src)
set(RSC ${CMAKE_CURRENT_SOURCE_DIR}/ressources)
set(FOR ${CMAKE_CURRENT_SOURCE_DIR}/forms)

include_directories(${HDR})

set(HDRS
    ${HDR}/PullBackupWindow.hpp
)

set(SRCS
    ${SRC}/main.cpp

    ${SRC}/PullBackupWindow.cpp
)

set(RSCS
)

set(FORS 
    ${FOR}/PullBackupWindow.xml
)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)

find_package(Qt5Widgets)

add_executable(FTPBackupPuller ${SRCS} ${HDRS} ${RSCS} ${FORS})

target_link_libraries(FTPBackupPuller Qt5::Widgets)

# Activate C++11
list(APPEND CMAKE_CXX_FLAGS "-std=c++11 -lrt ${Qt5Widgets_EXECUTABLE_COMPILE_FLAGS} ${CMAKE_CXX_FLAGS}")

if(${CMAKE_BUILD_TYPE} MATCHES "Debug")
    list(APPEND ${CMAKE_CXX_FLAGS} "-Wall -std=c++11 -lrt ${Qt5Widgets_EXECUTABLE_COMPILE_FLAGS} ${CMAKE_CXX_FLAGS}")
endif()
