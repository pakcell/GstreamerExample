cmake_minimum_required(VERSION 3.5)
project(GstreamerTest)

set(CMAKE_CXX_STANDARD  14)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -ggdb -Wall -fpermissive -fno-omit-frame-pointer")

include_directories(/opt/gstreamer-sdk/include/)
link_directories("/opt/gstreamer-sdk/lib")

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package (Threads)
find_package(PkgConfig REQUIRED)
pkg_check_modules(PC_LIBSOUP REQUIRED libsoup-2.4)
pkg_check_modules (GST          REQUIRED   gstreamer-1.0)
pkg_check_modules (GLIB2        REQUIRED   glib-2.0)
pkg_check_modules (GOBJ2        REQUIRED   gobject-2.0)
pkg_check_modules (GST_WEBRTC   REQUIRED   gstreamer-webrtc-1.0)
pkg_check_modules (GST_SDP      REQUIRED   gstreamer-sdp-1.0)
pkg_check_modules(JSON REQUIRED json-glib-1.0)

set(TEST_LIBRARIES
        ${GST_LIBRARIES}
        ${GST_WEBRTC_LIBRARIES}
        ${PC_LIBSOUP_LIBRARIES}
        ${GST_SDP_LIBRARIES}
        ${GLIB2_LIBRARIES}
        ${JSON_LIBRARIES}
        ${GOBJ2_LIBRARIES}
        Threads::Threads)

set(TEST_INCLUDE_DIRS
        ${GST_INCLUDE_DIRS}
        ${GLIB2_INCLUDE_DIRS}
        ${PC_LIBSOUP_INCLUDE_DIRS}
        ${JSON_INCLUDE_DIRS})

add_executable(gstreamerWebrtcExample GstreamerWebrtcExample.cpp)
target_include_directories(gstreamerWebrtcExample PRIVATE ${TEST_INCLUDE_DIRS})
target_link_libraries(gstreamerWebrtcExample
        ${TEST_LIBRARIES})
