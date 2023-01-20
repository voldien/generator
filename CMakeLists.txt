cmake_minimum_required(VERSION 3.9)
project(generator)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

include(GNUInstallDirs)

set(TARGET_NAME ${CMAKE_STATIC_LIBRARY_PREFIX}generator${SUFFIX}${CMAKE_STATIC_LIBRARY_SUFFIX})

message(STATUS "Target name is '${TARGET_NAME}'")

add_subdirectory(src)

if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
	add_subdirectory(images)
endif()

install(DIRECTORY include/generator DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
install(TARGETS generator${SUFFIX} DESTINATION ${CMAKE_INSTALL_LIBDIR})
