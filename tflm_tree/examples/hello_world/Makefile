SRC=$(wildcard *.cc)
OBJ=$(patsubst %.cc,%.o,$(SRC))

$(info $(OBJ))
TARGET:=hello

CROSS_COMPILE=arm-linux-musleabi-
CCFLAGS:=-c -march=armv7-a -mtune=cortex-a7 -ftree-vectorize -ffast-math -funwind-tables -fno-strict-aliasing -fcommon -msoft-float -Wall -O0 -gdwarf-2 -Woverloaded-virtual -fno-exceptions -fno-rtti -std=c++11
INCFLAGS:=-I../../ -I../../third_party/flatbuffers/include
LIBSFLAG:=-L../.. -ltfm

$(TARGET):$(OBJ)
	$(CROSS_COMPILE)g++ $^ $(LIBSFLAG) -o $@

%.o:%.cc
	$(CROSS_COMPILE)g++ $(CCFLAGS) $(INCFLAGS) $< -o $@

clean:
	rm -frv $(TARGET) $(OBJ)
