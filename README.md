suntans-plugin2
===============

A VisIt 2.x plugin for reading SUNTANS output in native proprietary format

Installation in Windows
--

For the precompiled, VisIt 2.7.3 Windows binaries, you have to have a compiler 
compatible with MS Visual Studio 2010.  There is a free MS Visual Studio 2010 Express
download - hopefully that works.

When installing the VisIt binaries, choose all users, enable plugin development,
and disable the TFT database reader.

    xml2cmake -clobber suntans2.xml
    xml2info -clobber suntans2.xml
    cmake -G "Visual Studio 10 Win64"
    
Unfortunately, the cmake command fails, as some of the paths have spaces, and
they are not properly enclosed by double quotes.  Even fixing that quote problem
(in PluginVsInstall.cmake), then I get an error that MS Visual Studio 2010 Express
does not support 64-bit.  It prints a URL for downloading the SDK necessary to
compile 64-bit.  After installing that, still gets a cmake error, something about
an empty list? PluginVsInstall.cmake line 406.  Based on visit bug 1644, this
is an issue with cmake >= 2.8.12.  At this point, cmake runs to completion, 
but devenv.exe is missing - may have to separately pull in the C++ part of
the Windows SDK.  Not sure where devenv.exe is, but opening the .sln file 
in the GUI works.  Now it gets a compile error due to the updated VTK API
regarding ghost cells.  Hopefully that's now taken care of with some 
CPP directives.  But regex libraries and some dll thing are undefined at the
link stage.  win32-regex is provided by visit.

Installation in Linux
----

Install a Visit binary for the platform closest to your platform.  The published
binaries tend to use older g++ compilers, so the best bet is often to just use executables
compiled with the newest g++.  You'll also need cmake.  Then:

    /path/to/visit/binaries/xml2info -clobber suntans2.xml
    /path/to/visit/binaries/xml2cmake -clobber suntans2.xml
    cmake .
    make
  
