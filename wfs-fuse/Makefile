LIB=-L../
INC=-I../
CXXFLAGS=$(INC) -c -Wall -Werror -std=c++14 -D_FILE_OFFSET_BITS=64
LDFLAGS=$(LIB) -lfuse -lwfs -lboost_system -lboost_filesystem -lboost_program_options -lcryptopp -lstdc++
SOURCES=wfs-fuse.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=wfs-fuse

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS) ../libwfs.a 
	$(CXX) $(OBJECTS) $(LDFLAGS) -o $@

.cpp.o:
	$(CXX) $(CXXFLAGS) $< -o $@

depend: .depend

.depend: $(SOURCES)
	rm -f .depend
	$(CXX) $(CXXFLAGS) -MM $^ > .depend

include .depend

.PHONY: clean
clean:
	rm -f $(OBJECTS) $(EXECUTABLE) .depend
