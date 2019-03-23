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
pkg-config needs .pc files for all library dependecies located in standard directories or identified
by PKG_CONFIG_PATH

	$ man pkg-config 

OPENCV INSTALL FOR UBUNTU
-------------------------

***Reference:***  
https://www.learnopencv.com/install-opencv-3-4-4-on-ubuntu-16-04/

***Update packages:***

	$ sudo apt-get update
	$ sudo apt-get upgrade


***OS libraries:***  
Remove any previous installations of x264 

	$ sudo apt-get remove x264 libx264-dev
 
***Dependencies now:***
 
	$ sudo apt-get install build-essential checkinstall cmake pkg-config yasm
	$ sudo apt-get install git gfortran
	$ sudo apt-get install libjpeg8-dev libjasper-dev libpng12-dev
 
If you are using Ubuntu 14.04

	$ sudo apt-get install libtiff4-dev
I
If you are using Ubuntu 16.04

	$ sudo apt-get install libtiff5-dev
 	$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
	$ sudo apt-get install libxine2-dev libv4l-dev
	$ sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
	$ sudo apt-get install qt5-default libgtk2.0-dev libtbb-dev
	$ sudo apt-get install libatlas-base-dev
	$ sudo apt-get install libfaac-dev libmp3lame-dev libtheora-dev
	$ sudo apt-get install libvorbis-dev libxvidcore-dev
	$ sudo apt-get install libopencore-amrnb-dev libopencore-amrwb-dev
	$ sudo apt-get install x264 v4l-utils
 
***Optional dependencies:***

	$ sudo apt-get install libprotobuf-dev protobuf-compiler
	$ sudo apt-get install libgoogle-glog-dev libgflags-dev
	$ sudo apt-get install libgphoto2-dev libeigen3-dev libhdf5-dev doxygen

***Python libraries:***

	$ sudo apt-get install python-dev python-pip python3-dev python3-pip
	$ sudo -H pip2 install -U pip numpy
	$ sudo -H pip3 install -U pip numpy
	$ sudo pip2 install virtualenv virtualenvwrapper
	$ sudo pip3 install virtualenv virtualenvwrapper
	$ echo "# Virtual Environment Wrapper"  >> ~/.bashrc
	$ echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bashrc
	$ source ~/.bashrc
  
***Python 2***

	$ mkvirtualenv facecourse-py2 -p python2
	$ workon facecourse-py2
  	$ pip install numpy scipy matplotlib scikit-image scikit-learn ipython
	$ deactivate

***Python 3***

	$ mkvirtualenv facecourse-py3 -p python3
	$ workon facecourse-py3
	$ pip install numpy scipy matplotlib scikit-image scikit-learn ipython
	$ deactivate

***OpenCV Source:***

	$ git clone https://github.com/opencv/opencv.git
	$ cd opencv 
	$ git checkout 3.3.1 
	$ cd ..

	$ git clone https://github.com/opencv/opencv_contrib.git
	$ cd opencv_contrib
	$ git checkout 3.3.1
	$ cd ..

	$ cd opencv
	$ mkdir build
	$ cd build

	$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
      -D CMAKE_INSTALL_PREFIX=/usr/local \
      -D INSTALL_C_EXAMPLES=ON \
      -D INSTALL_PYTHON_EXAMPLES=ON \
      -D WITH_TBB=ON \
      -D WITH_V4L=ON \
      -D WITH_QT=ON \
      -D WITH_OPENGL=ON \
      -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
      -D BUILD_EXAMPLES=ON ..

***OpenCV Build:***

	$ make -j4
	$ sudo make install
	$ sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv.conf'
	$ sudo ldconfig

***Link Python Virtuals:***

	$ find /usr/local/lib/ -type f -name "cv2*.so"

***Python 2***

	$ cd ~/.virtualenvs/facecourse-py2/lib/python2.7/site-packages
	$ ln -s /usr/local/lib/python2.7/dist-packages/cv2.so cv2.so
  
***Python 3***

	$ cd ~/.virtualenvs/facecourse-py3/lib/python3.6/site-packages
	$ ln -s /usr/local/lib/python3.6/dist-packages/cv2.cpython-36m-x86_64-linux-gnu.so cv2.so
