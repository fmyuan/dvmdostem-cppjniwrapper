dvmdostem-jnicppwrapper
============
Core codes of DVMDOSTEM, wrapped with JNI for producing a dynamical-linked library to be used by Java GUI (e.g. Calibrator and Runner) 

Workflow
-----------

(1) copy the core model codes to here
(2) There is an extra cpp module (temccjava.cpp, temccjava.h) to pass critical data between Java codes and C++ codes
(3) Four (4) *.i files to be used by swig program to generate the JNI c++ wrapper, by running the following command (if available in your system)
swig -java -c++ -module temcore -o TEMwrapper.cpp -outdir ../../DVMDOSTEMrunjava/src/TEMJNI -package TEMJNI TEMrun.i


Documentation
-------------

Compile
---------
This project requires java JNI for the targetted OS. The directory holding this JNI header and others is hard-weired in swig-generated 'TEMwrapper.cpp'. It may be needed to update it if the compilation would complains about it. 

$ make

Run
---------
The project generates a dynamic-linked library called "temcore.dll" (windows OS) or "libtemcore.dylib" (mac OS) or "libtemcore.so" (linux), upon the system you run 'swig'.

Copy this library to the Java interface GUI package (*.jar), which then can be called by the Java coded Calibrator or Runner.
