CXX      = g++
CXXFLAGS = -Wall -Wextra
#CXX = clang++
#CXXFLAGS = -Weverything -Wno-c++11-extensions -std=gnu++11

EXEC     = app
SRC      = $(wildcard src/*.cpp)
OBJ      = $(patsubst src/%.cpp,obj/%.o,$(SRC))
DEP      = $(OBJ:.o=.d)


all: info print_compilation $(EXEC) open


-include $(DEP)


info:
	@echo "\n-> makefile info"
	@echo "CXX:      "$(CXX)
	@echo "CXXFLAGS: "$(CXXFLAGS)
	@echo "EXEC:     "$(EXEC)
	@echo "SRC:      "$(SRC)
	@echo "OBJ:      "$(OBJ)
	@echo "DEP:      "$(DEP)


print_compilation:
	@echo "\n-> compilation"


$(EXEC): $(OBJ)
	$(CXX) $^ -o $(EXEC)


obj/%.o : src/%.cpp
	$(CXX) $(CXXFLAGS) -MMD -MP -c $< -o $@


open:
	@echo "\n-> launch" $(EXEC) ""
	@./$(EXEC)


clean:
	@echo "\n-> cleaning..."
	rm -f obj/*.o
	rm -f obj/*.d
	rm -f $(EXEC)


.PHONY: all info clean



# $(patsubst pattern,replacement,text)
# $^ : contains the list of dependencies
# $< : contains the name of the first dependency
# $@ : contains the target name
# a .PHONY target is simply a target that is always out-of-date (eg not a file)


