CXXFLAGS := -Wall -Werror
CXXFLAGS := $(CXXFLAGS) -std=c++11 -g

TSP-GOOD:main.o graph.o
	g++ $(CXXFLAGS) -o TSP-GOOD main.o graph.o

TSP: main.o graph.o
	g++ $(CXXFLAGS) -o TSP main.o graph.o

unit-test: graph.o test_functions.o
	$(CXX) $(CXXFLAGS)-o $@ $^ -L. -lgtest -lpthread

main.o: main.cpp graph.h
	g++ $(CXXFLAGS) -c main.cpp

graph.o: graph.cpp graph.h
	$(CXX) $(CXXFLAGS) -c $< graph.cpp

memtest: TSP
	valgrind --leak-check=full ./TSP

clean:
	-rm -f *~
	-rm -f $(TARGETS)
	-rm -f *.o