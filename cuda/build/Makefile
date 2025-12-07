MPICC = mpicxx
NVCC = nvcc

VPATH = ../src

SRC  := $(wildcard $(VPATH)/*.cu)
OBJS := $(patsubst %.cu,%.o,$(notdir $(SRC)))

MPI_CFLAGS  := $(shell $(MPICC) --showme:compile)
MPI_LDFLAGS := $(shell $(MPICC) --showme:link)

CFLAGS = -DUSE_MPI -O3 $(MPI_CFLAGS)
LDFLAGS = -lm -lstdc++ $(MPI_LDFLAGS)

all: lulesh
lulesh: $(OBJS)
	$(NVCC) -o $@ $(OBJS) $(LDFLAGS)

%.o: %.cu
	$(NVCC) $(CFLAGS) -I$(VPATH) -c $< -o $@

clean:
	rm -f $(OBJS) lulesh
