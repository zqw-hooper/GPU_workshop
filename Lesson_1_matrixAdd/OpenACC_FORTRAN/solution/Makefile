# Compilers and linkers
F90=nvfortran

# Compilation flags
FFLAGS= -O3 -Wall -Mfree

ifeq ($(_OPENACC),true)
ACCFLAGS= -acc -gpu=cc60,cc70,managed -Minfo=all -I${NVHPC_ROOT_PATH}/include
else 
ACCFLAGS=
endif

# Description of necessary files and binaries
# List of object files separated by spaces (e.g. main.o device.o)
OBJECTS= matrix_add.o 
# The binary to be built by this Makefile
BINARY= matrix_add.exe


all: $(BINARY) 

$(BINARY): $(OBJECTS)
	$(F90) -o $(BINARY) $(OBJECTS) $(ACCFLAGS) 

%.o: %.f90 Makefile
	$(F90) -c $(FFLAGS) $(ACCFLAGS) $<




clean:
	rm *.o $(BINARY)

