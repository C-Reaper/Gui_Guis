# Project README

## Overview
- The project is a simple GUI application written in C. It features multiple buttons displayed on a window, and reacts to user interactions.

## Features
- **Multiple Buttons**: Displaying three buttons arranged horizontally.
- **Event Handling**: Basic event handling for button clicks (placeholder functions).
- **Cross-Platform Compilation**:
  - Linux: Uses X11 library for GUI.
  - Windows: Uses WINAPI for GUI.
  - Wine: Cross-compiles to Windows executable.
  - Web: Compiles to WebAssembly using Emscripten.

## Project Structure
### Prerequisites
- C/C++ Compiler and Debugger (GCC, Clang)
- Make utility
- Standard development tools
- Libraries:
  - Linux: X11
  - Windows: WINAPI
  - Wine: User32, GDI32, Winmm
  - Web: SDL2

## Build & Run
### Linux
To build and run the project on Linux:
```sh
cd <Project>
make -f Makefile.linux all
./build/Main
```

### Windows
To build and run the project on Windows:
```sh
cd <Project>
make -f Makefile.windows all
./build/Main.exe
```

### Wine
To cross-compile for Windows using Wine:
```sh
cd <Project>
make -f Makefile.wine all
wine64 ./build/Main.exe
```

### Web
To build and run the project on the web using Emscripten:
```sh
cd <Project>
emcc -O0 -msimd128 -mavx2 -std=gnu17 -Wall -Wno-unused -Wshadow -Werror -Isrc -D_WEB -sINITIAL_MEMORY=169082880 src/*.c -o build/index.html --no_browser --port 8080
```
Then open `http://localhost:8080` in a web browser to view the application.

## Clean Build
```sh
make -f Makefile.(os) clean
make -f Makefile.(os) all
```

## Executable
The built executable is located in the `build/` directory.