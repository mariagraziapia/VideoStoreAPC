# Makefile for VideoStore refactoring example

ifndef UNAMEM
  UNAMEM := $(shell uname -m)
endif
$(info '$(UNAMEM)')

CXX        = g++
LD         = $(CXX)
OPT        = -g

# Environment variable to be set, where gtest is installed
# GTESTPATH = /Users/pia/Documents/g4dev/googletest/gtest_install/
# GTESTPATH=/usr/local

ifeq ($(HOSTNAME), naf-school01.desy.de)
    GTESTPATH=/usr
endif

ifeq ($(HOSTNAME), naf-school02.desy.de)
    GTESTPATH=/usr
endif

GINCS = -I $(GTESTPATH)/include

ifeq ($(UNAMEM), x86_64)
	GLIBS = -L $(GTESTPATH)/lib64 -lgtest -lpthread
else
	GLIBS = -L $(GTESTPATH)/lib -lgtest -lpthread
endif

CXXFLAGS   = -std=c++17 -Wall $(OPT) -fPIC $(GINCS)

LDFLAGS    =

SOURCES    = Customer.cc Movie.cc Rental.cc Price.cc RegularPrice.cc NewReleasePrice.cc ChildrensPrice.cc 
TESTSRC    = testVideoStore.cc
OBJECTS    = $(SOURCES:.cc=.o) $(TESTSRC:.cc=.o)
EXECUTABLE = $(basename $(TESTSRC) )

all: $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS) 
	$(LD) $(LDFLAGS) -o $@ $^ $(GLIBS)
	LD_LIBRARY_PATH=$(PWD) ./$@


clean:
	rm -f $(OBJECTS) $(EXECUTABLE)

