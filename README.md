# OpenCV-RS
### OpenCV (with opencv_contrib) from Embarcadero Rad Studio Tokyo 10.2.3
#### Only Clang compiler.

#### How to build and install.

For example - folder path "C:\OpenCV\opencv_3.2.0"

* Load or clone this repository. Go to the directory "C:\OpenCV\opencv_3.2.0" and create folder "build".
* Run CMake and specify next options:
* "Where is the source code:"   	"C:\OpenCV\opencv_3.2.0";
* "Where to build the binaries:"	"C:\OpenCV\opencv_3.2.0\build";
* Click configure button, select "Borland Makefiles" and "Specify native compilers".
* Next, specify the path to bcc32c.exe (Clang) for c++ and c, click finish.

After configuration, next steps - find and disable options:
* WITH_WEBP
* WITH_JASPER
* WITH_IPP
* WITH_OPENEXR
* BUILD_TESTS
* BUILD_PERF_TESTS
* BUILD_SHARED_LIBS

enable options:
* OPENCV_ENABLE_NONFREE
* OPENCV_EXTRA_MODULES_PATH     specify the path to "C:\OpenCV\opencv_contrib_3.2.0\modules"

new configure project.

* After configarutation, find and disable options:
* BUILD_PROTOBUF
* BUILD_opencv_dnn

new configure project and generate.

* Run Rad Studio Command Promt and go to the directory "C:\OpenCV\opencv_3.2.0\build".

make install.

* For Release build new configure and make project with option:
* CMAKE_BUILD_TYPE - Release.

### How to use.

* Open Tools->Options->C++ Options->Paths and Directories, select "32-bit Windows" "Compiler". 
* Add to "System include path": 
* "C:\OpenCV\opencv_3.2.0\build\install";
* "C:\OpenCV\opencv_3.2.0\build\install\include";
* Add to "Library path":
* "C:\OpenCV\opencv_3.2.0\build\install\staticlib";
  
Create new c++ project.
* Open Project->Options->C++ Compiler and disable "Use 'classic' Borland compiler".
* Add to your project all static libs in folder
* "C:\OpenCV\opencv_3.2.0\build\install\staticlib".

It's ready - add requir headers, write your code and run project ;) 

### ToDo

Fix temporary hack solution:
* 1 - file opencv\modules\ts\src\ts_gtest.cpp, line 5028 function "static bool PortableLocaltime(time_t seconds, struct tm* out)";
* 2 - file opencv_contrib\modules\datasets\src\util.cpp, line 83 function "void getDirList(const string &dirName, vector<string> &fileNames)".
