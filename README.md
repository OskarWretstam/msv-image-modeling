# msv-image-modeling
Building an image based modeling application based on insight3d

COMPILING UNDEX LINUX
---------------------

To compile insight3dng under Linux, you must have the following libraries: 

	- opencv
	- opengl
	- SDL
	- libxml2 (to parse xml files)
	- lapack and blas (to do some math)
	- libgtk+-2.0

And this should be pretty much everything. Also, pkg-config should know about those libraries. 

Makefile and source code is in the "insight3d" subdirectory. There's no configuration, just execute "make" in the "insight3d" subdirectory. 