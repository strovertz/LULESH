MPICC = mpicxx
NVCC = nvcc

VPATH = ../src

SRC  := $(wildcard $(VPATH)/*.cu)
OBJS := $(patsubst %.cu,%.o,$(notdir $(SRC)))


CFLAGS = -O3 
LDFLAGS = -lm -lstdc++ 
all: lulesh
lulesh: $(OBJS)
	$(NVCC) -o $@ $(OBJS) $(LDFLAGS)

%.o: %.cu
	$(NVCC) $(CFLAGS) -I$(VPATH) -c $< -o $@

clean:
	rm -f $(OBJS) lulesh
