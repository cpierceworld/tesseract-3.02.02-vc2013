set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR})

# Change to wherever "tesseract-3.02.02-vc2013" was installed
SET(Tesseract_DIR "C:/tesseract-3.02.02-vc2013")

if (CMAKE_CL_64)
    set(ARCH_DIR "x64")
else()
    set(ARCH_DIR "Win32")
endif()

# Or use "$(Platform)" as ARCH_DIR
# which is Visual Studio 2013 variable
# (should resolve to selected "Platform" of "Win32" or "x64")
# set(ARCH_DIR "$(Platform)")


SET(Tesseract_RELEASE_LIB "${Tesseract_DIR}/lib/${ARCH_DIR}/Release")
SET(Tesseract_DEBUG_LIB   "${Tesseract_DIR}/lib/${ARCH_DIR}/Debug")


message(STATUS "Tesseract:   YES")
SET(Tesseract_FOUND 1)
SET(HAVE_TESSERACT 1)

add_definitions( -DWINDOWS)
add_definitions( -DNOMINMAX)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/text_config.hpp.in
               ${CMAKE_BINARY_DIR}/text_config.hpp @ONLY)

include_directories(${CMAKE_CURRENT_BINARY_DIR})

set(the_description "Text Detection and Recognition")
ocv_define_module(text opencv_ml opencv_highgui opencv_imgproc opencv_core opencv_features2d WRAP python)

include_directories(${Tesseract_DIR}/include)
target_link_libraries(opencv_text 
                      optimized ${Tesseract_RELEASE_LIB}/libtesseract302.lib debug ${Tesseract_DEBUG_LIB}/libtesseract302d.lib
                      optimized ${Tesseract_RELEASE_LIB}/liblept168.lib debug ${Tesseract_DEBUG_LIB}/liblept168d.lib)
					  

