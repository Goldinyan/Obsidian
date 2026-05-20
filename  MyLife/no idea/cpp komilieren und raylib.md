g++ main.cpp -o main -lraylib -framework CoreVideo -framework IOKit -framework Cocoa -framework OpenGL

Makefile

CXX = g++
CXXFLAGS = -Wall -std=c++17
# Suchpfade für Homebrew (wichtig auf Apple Silicon/M1/M2/M3)
LDFLAGS = -L/opt/homebrew/lib -lraylib -framework CoreVideo -framework IOKit -framework Cocoa -framework OpenGL
CPPFLAGS = -I/opt/homebrew/include

TARGET = game

all: $(TARGET)

$(TARGET): main.cpp
	$(CXX) $(CXXFLAGS) $(CPPFLAGS) main.cpp -o $(TARGET) $(LDFLAGS)

clean:
	rm -f $(TARGET)



M