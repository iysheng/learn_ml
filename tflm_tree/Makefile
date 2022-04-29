CC_SRC=$(wildcard tensorflow/lite/c/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/core/api/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/kernels/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/kernels/internal/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/kernels/internal/optimized/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/kernels/internal/reference/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/micro/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/micro/arena_allocator/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/micro/kernels/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/micro/memory_planner/*.cc)
CC_SRC+=$(wildcard tensorflow/lite/schema/*.cc)

CC_OBJS:=$(patsubst %.cc,%.o,$(CC_SRC))
TARGET:=libtfm.a

CROSS_COMPILE:=arm-linux-musleabi-

CCFLAGS:=-c -march=armv7-a -mtune=cortex-a7 -ftree-vectorize -ffast-math -funwind-tables -fno-strict-aliasing -fcommon -msoft-float -Wall -O0 -gdwarf-2 -Woverloaded-virtual -fno-exceptions -fno-rtti -std=c++11
INCFLAGS:=-I. -Ithird_party/flatbuffers/include
INCFLAGS+=-Ithird_party/gemmlowp
INCFLAGS+=-Ithird_party/ruy

$(TARGET):$(CC_OBJS)
	$(CROSS_COMPILE)ar -rsv $@ $^

%.o:%.cc
	$(CROSS_COMPILE)g++ $(CCFLAGS) $(INCFLAGS) $^ -o $@

clean:
	rm -frv $(TARGET) $(CC_OBJS)
