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

Also, pkg-config should know about those libraries. 

To build, run make in insight3d subdirectory.
For issues with dependecies refer to build-deps.txt
