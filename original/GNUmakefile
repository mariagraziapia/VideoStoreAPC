# Makefile for VideoStore refactoring example

ifndef UNAMEM
  UNAMEM := $(shell uname -m)
endif

$(info '$(UNAMEM)')

# $(info '$(arch)')

# Options for various architectures
# CXX        = g++
# CXX        = g++ -arch arm64
# CXX        = clang++ 
# CXX        = clang++ -arch arm64

# ifeq ($(UNAMEM),arm64)
# ifeq (arch,arm64)
#  CXX        = g++ -arch arm64
#else
CXX        = g++
#endif

LD         = $(CXX)
OPT        = -g

# Environment variable to be set, where gtest is installed
# GTESTPATH=/usr/local

ifeq ($(HOSTNAME), naf-school01.desy.de)
    GTESTPATH=/usr
endif

ifeq ($(HOSTNAME), naf-school02.desy.de)
    GTESTPATH=/usr
endif

GINCS = -I $(GTESTPATH)/include
GLIBS = -L $(GTESTPATH)/lib -lgtest -lpthread

CXXFLAGS   = -std=c++17 -Wall $(OPT) -fPIC $(GINCS)

LDFLAGS    =

SOURCES    = Customer.cc Movie.cc 
TESTSRC    = testVideoStore.cc
OBJECTS    = $(SOURCES:.cc=.o) $(TESTSRC:.cc=.o)
EXECUTABLE = $(basename $(TESTSRC) )

all: $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS) 
	$(LD) $(LDFLAGS) -o $@ $^ $(GLIBS)
	LD_LIBRARY_PATH=$(PWD) ./$@


clean:
	rm -f $(OBJECTS) $(EXECUTABLE)

