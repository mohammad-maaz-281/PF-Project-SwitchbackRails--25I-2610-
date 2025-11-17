# ============================================================================
# Makefile for Switchback Rails
# ============================================================================

CXX = g++
CXXFLAGS = -std=c++11 -Wall -Wextra -g -mconsole
SFML_INCLUDE = -I"C:/Users/moham/OneDrive/Desktop/SFML-2.5.1/include"
SFML_LIB = -L"C:/Users/moham/OneDrive/Desktop/SFML-2.5.1/lib"
SFML_FLAGS = -lsfml-graphics -lsfml-window -lsfml-system

# Automatically find all .cpp files in core/ and sfml/ directories
CORE_SRCS = $(wildcard core/*.cpp)
SFML_SRCS = $(wildcard sfml/*.cpp)
ALL_SRCS = $(CORE_SRCS) $(SFML_SRCS)

# Generate object file names from source files
ALL_OBJS = $(ALL_SRCS:.cpp=.o)

# Output executable
TARGET = switchback_rails.exe

# Default target
all: $(TARGET)

# Link executable
$(TARGET): $(ALL_OBJS)
	$(CXX) $(CXXFLAGS) -o $@ $^ $(SFML_LIB) $(SFML_FLAGS)
	@echo "Build complete! Run with: ./$(TARGET)"

# Compile source files (pattern rule for all .cpp files)
%.o: %.cpp
	$(CXX) $(CXXFLAGS) $(SFML_INCLUDE) -c $< -o $@

# Clean build artifacts
clean:
	-del /Q core\*.o sfml\*.o $(TARGET) 2>nul
	-del /Q out\*.csv out\*.txt 2>nul
	@echo "Clean complete!"

# Run the complex network level (default)
run: $(TARGET)
	./$(TARGET) data/levels/complex_network.lvl

# Show help
help:
	@echo "Switchback Rails - Makefile"
	@echo ""
	@echo "Targets:"
	@echo "  make          - Build the project"
	@echo "  make run      - Build and run Complex Railway Network"
	@echo "  make clean    - Remove build artifacts"
	@echo "  make help     - Show this help message"
	@echo ""
	@echo "Found source files:"
	@echo "  Core: $(CORE_SRCS)"
	@echo "  SFML: $(SFML_SRCS)"

.PHONY: all clean run help

