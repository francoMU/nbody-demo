CXX = icpc
COMPFLAGS = -std=c++11 -O2   
OPTFLAGS = -xAVX2
OMPFLAGS = -qopenmp-simd
REPFLAGS = -qopt-report=5 -qopt-report-filter="GSimulation.cpp,130-220" 
INCLUDES = 

CXXFLAGS = $(COMPFLAGS) $(OPTFLAGS) $(REPFLAGS) $(OMPFLAGS) 

SOURCES = GSimulation.cpp main.cpp

.SUFFIXES: .o .cpp

##########################################
OBJSC = $(SOURCES:.cpp=.o)
##########################################

EXEC=nbody.x

all: cpu

%.o: %.cpp
	$(info )
	$(info Compiling the object file for CPU: )
	$(CXX) $(CXXFLAGS) $(INCLUDES) -c $< -o $@ 

cpu: $(OBJSC)
	$(info )
	$(info Linking the CPU executable:)
	$(CXX) $(CXXFLAGS) $(INCLUDES) -o $(EXEC) $(OBJSC)
	
run: 
	$(info )
	$(info Run the default test case on CPU: )
	./nbody.x 
	
clean: 
	rm -f $(OBJSC) nbody.x *.optrpt 

