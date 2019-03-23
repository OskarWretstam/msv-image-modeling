SOURCES=$(wildcard *.cpp)
OBJECTS=$(patsubst %.cpp,%.o,$(SOURCES))
ANN_INCLUDE= -I./ann_1.1.1/include/
CPP_FLAGS=-O3

all: insight3d

insight3dold: $(OBJECTS) sift_detector
	g++ $(CPP_FLAGS) -o insight3d *.o `pkg-config --libs opencv libxml-2.0 sdl gtk+-2.0` ./sift/lib/libfeat.a $(AGARLIB) -llapack -lblas -lGL -lGLU ./sba/libsba.a ./ann_1.1.1/lib/libANN.a

insight3d: $(OBJECTS) sift_detector
	g++ $(CPP_FLAGS) -o insight3d *.o `pkg-config --libs opencv libxml-2.0 sdl gtk+-2.0` ./sift/lib/libfeat.a $(AGARLIB) ./sba/libsba.a -llapack -lblas -lGL -lGLU -lgdk-x11-2.0 -lpthread ./ann_1.1.1/lib/libANN.a

insight3dfailed: $(OBJECTS) sift_detector
	g++ $(CPP_FLAGS) -o insight3d *.o `pkg-config --libs opencv libxml-2.0 sdl gtk+-2.0` -LGDK-x11-2.0-2.0 -lgobject ./sift/lib/libfeat.a -LGL -lGLU -LSBA -LSBA -llapack -lblas ./ann_1.1.1/lib/libANN.a /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so -lf2c -lm

sift_detector:
	make -C ./sift libfeat.a
	make -C ./ann_1.1.1 linux-g++
	make -C ./sba

%.o: %.cpp
	g++ $(CPP_FLAGS) -c `pkg-config --cflags opencv libxml-2.0 sdl gtk+-2.0` $(ANN_INCLUDE) $<

clean: 
	rm -f *.o
	rm -f ./insight3d


