CC=g++
CFLAGS=-c -Wall
LDFLAGS=
SOURCES=Customer.cc Movie.cc Rental.cc RegularPrice.cc NewReleasePrice.cc ChildrensPrice.cc fowler.cc
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=fowler

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS) 
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.cpp.o:
	$(CC) $(CFLAGS) $< -o $@