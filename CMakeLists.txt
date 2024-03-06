cmake_minimum_required(VERSION 3.21)
project(A)

if (NOT TARGET ${PROJECT_NAME})
    set(B_ROOT "${CMAKE_CURRENT_SOURCE_DIR}/../repoB/" CACHE PATH "Path to B")
    add_subdirectory(${B_ROOT} ${CMAKE_CURRENT_BINARY_DIR}/B)
    set(C_ROOT "${CMAKE_CURRENT_SOURCE_DIR}/../repoC/" CACHE PATH "Path to C")
    add_subdirectory(${C_ROOT} ${CMAKE_CURRENT_BINARY_DIR}/C)
    add_executable(${PROJECT_NAME}
        ${PROJECT_NAME}/a.cpp
    )
    target_link_libraries(${PROJECT_NAME} PUBLIC B C)
endif()