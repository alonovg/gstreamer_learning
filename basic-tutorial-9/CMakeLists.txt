cmake_minimum_required(VERSION 3.16)

project(gstreamer_test_cpp)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GST REQUIRED gstreamer-1.0)

pkg_check_modules(GST_PBUTILS REQUIRED gstreamer-pbutils-1.0)

include_directories(${GST_INCLUDE_DIRS})
include_directories(${GST_PBUTILS_INCLUDE_DIRS})

link_directories(${GST_LIBRARY_DIRS})
link_directories(${GST_PBUTILS_LIBRARY_DIRS})

add_executable(${PROJECT_NAME} basic-tutorial-9/basic-tutorial-9.c)

target_link_libraries(${PROJECT_NAME} ${GST_LIBRARIES} ${GST_PBUTILS_LIBRARIES})

