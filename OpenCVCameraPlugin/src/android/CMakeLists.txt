cmake_minimum_required(VERSION 3.4.1)
set(CMAKE_VERBOSE_MAKEFILE ON)

add_library( BVDocCapLib SHARED src/main/cpp/scanlib.cpp )

find_library( jnigraphics-lib jnigraphics )

include_directories(SYSTEM /Users/admin/Projetos/Android/opencv-android/sdk/native/jni/include )

add_library( cv_core-lib SHARED IMPORTED)
set_target_properties( cv_core-lib
        PROPERTIES IMPORTED_LOCATION
        "/Users/admin/Projetos/Android/opencv-android/sdk/native/libs/${ANDROID_ABI}/libopencv_core.so" )

add_library( cv_imgproc-lib SHARED IMPORTED)
set_target_properties( cv_imgproc-lib
        PROPERTIES IMPORTED_LOCATION
        "/Users/admin/Projetos/Android/opencv-android/sdk/native/libs/${ANDROID_ABI}/libopencv_imgproc.so" )

add_library( cv_imgcodecs-lib SHARED IMPORTED)
set_target_properties( cv_imgcodecs-lib
        PROPERTIES IMPORTED_LOCATION
        "/Users/admin/Projetos/Android/opencv-android/sdk/native/libs/${ANDROID_ABI}/libopencv_imgcodecs.so" )

target_link_libraries( BVDocCapLib ${jnigraphics-lib} cv_core-lib cv_imgproc-lib cv_imgcodecs-lib log)