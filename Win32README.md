# Windows Build Instructions #

To build LibOFA, you only need LibFFTW. If you want to build the complete example that actually generates a PUID from a .WAV file, you will need to install Expat and LibCURL as well.

# FFTW #

  * Copy LibFFTW tarball to paralell dir.
  * undef #FFTW\_DLL
  * compile

# EXPAT #

Download the Expat XML parser from here:

http://sourceforge.net/project/showfiles.php?group_id=10127&package_id=11277

Unzip the contents into a directory called, "libcurl" in the same directory where you placed LibOFA. See the directory structure section below for additional details on this.

# LIBCURL #

Download the package from:

http://curl.haxx.se/latest.cgi?curl=win32-devel

Unzip the contents into a directory called, "libcurl" in the same directory where you placed LibOFA. See the directory structure section below for additional details on this.

Inside of libcurl\lib run:

lib.exe /def:libcurl-3.def

To generate the import library needed by MSVC++. Make sure that the "lib.exe" tool is in your search path.

# Directory Structure #

In order to get the project to compile from the Visual Studio .NET solution, you will need to set up a directory structure that looks like this:

```
C:\whatever
   libofa
      |---lib
      |    |---AFLIB
      |    |---JAMA
      |---include
      |    |---ofa1    ; contains ofa.h
      |---examples
      |---win32        ; contains windows build files, libofa.def
      |    |---Release ; contains the libofa.dll, libofa.lib after build (in release mode)
      |    |---Debug   ; contains the same as above, but in debug mode
      |   . . .
   expat
      |---Source
      |     |---Libs   ; contains expat.h, libexpat.def
      |     . . .
   libfftw3            ; Has no subdirs, contains libfftw3-3.def, libfftw3-3.dll, libfftw3.h
      |      
   libcurl
      |---bin
      |---docs
      |---include      
      |     |---curl   ; contains curl.h
      |---lib          ; contains libcurl-3.def, libcurl-3.dll
```

# Building LibOFA #

Open libofa\win32\libofa.sln in MSVC++ and build from there. If all the dependencies were installed and placed into the right structure, LibOFA will build for you.