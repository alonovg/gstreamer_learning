cmake_minimum_required(VERSION 3.16)

project(gstreamer_test_cpp) #Project name

set(CMAKE_CXX_STANDARD 14) #setting C++ 14 standard

find_package(PkgConfig REQUIRED)

pkg_check_modules(GTK REQUIRED gtkmm-3.0)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

include_directories(${GTK3_INCLUDE_DIRS})

link_directories(${GTK3_LIBRARY_DIRS})

add_definitions(${GTK3_CFLAGS_OTHER})

pkg_check_modules(GSTREAMER REQUIRED gstreamer-1.0)

#including GStreamer header files directory
include_directories(
        ${GLIB_INCLUDE_DIRS}
        ${GSTREAMER_INCLUDE_DIRS}
)

#linking GStreamer library directory
link_directories(
        ${GLIB_LIBRARY_DIRS}
        ${GSTREAMER_LIBRARY_DIRS}
)

#building target executable
add_executable(${PROJECT_NAME} basic-tutorial-5/basic-tutorial-5.c)

#linking Gstreamer library with target executable
target_link_libraries(${PROJECT_NAME} ${GSTREAMER_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${GTKMM_LIBRARIES})
target_link_libraries(${PROJECT_NAME} ${GTK3_LIBRARIES})

target_compile_definitions(${PROJECT_NAME} PRIVATE ${GTKMM_CFLAGS_OTHER})
