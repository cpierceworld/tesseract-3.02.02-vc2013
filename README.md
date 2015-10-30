# tesseract-3.02.02-vc2013
Tesseract for opencv_text in Visual Studio 2013

Tesseract 3.02.02 with Leptonica 1.68 compiled in Visual Studio 2013 (32 and 64 bit)

For use with OpenCV 3.0.0 "Scene Text Detection" (opencv_text) contrib module compiled with Visual Studio 2013.

To compile with OpenCV Contrib "text" module:
* Get the source for OpenCV Contrib source (https://github.com/Itseez/opencv_contrib)
* Replace the "CMakeLists.txt" in the OpenCV Contrib source's "modulles\text" with the file from this project ("opencv_contrib-3.0.0\modules\text\CMakeLists.txt")
* Edit the "CMakeLists.txt" that you copied into contrib source to change the "Tesseract_DIR" variable to point to wherever you checked this project out to.
* Do the OpenCV build (with OPENCV_EXTRA_MODULES_PATH) as usual...

To use once compiled, put the correct "libtesseract302.dll" adn "liblept168.dll" in your PATH, the same way you put the OpenCV dlls (specifically the "opencv_text300.dll") in your path (The correct being either the one in the "bin\Win32" or "bin\x64" folder for 32 or 64 bit respectivly.  Use the dlls in "Debug" for debug builds, "Release" for optimized (release) builds).


