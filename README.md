suntans-plugin2
===============

A VisIt 2.x plugin for reading SUNTANS output in native proprietary format

Installation in Windows
--

For the precompiled, VisIt 2.7.3 Windows binaries, you have to have a compiler 
compatible with MS Visual Studio 2010.  There is a free MS Visual Studio 2010 Express
download - hopefully that works.

Installation in Linux
----

Install a Visit binary for the platform closest to your platform.  The published
binaries tend to use older g++ compilers, so the best bet is often to just use executables
compiled with the newest g++.  You'll also need cmake.  Then:

    /path/to/visit/binaries/xml2info -clobber suntans2.xml
    /path/to/visit/binaries/xml2cmake -clobber suntans2.xml
    cmake .
    make
  
