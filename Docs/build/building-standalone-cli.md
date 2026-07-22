# Building NetDust Standalone CLI

Here is the step by step guide to compiling a cross platform, standalone NetDust application for both Linux and macOS:

> [!IMPORTANT]
> - Ensure you have a C++17 compatible compiler (`g++` or `clang++`) installed on your system.
> - The `xxd` command line utility must be available (pre installed by default on macOS and most Linux distributions).

## 1. Project Directory Setup

Make sure all required C++ source files and `.nd` script files are placed together in the root directory before building:

* `main.cpp` - Minimal standalone application entry point
* `NetDustInterpreter.cpp` / `.h` - Core VM parser engine
* `NativeLibraryRegistry.cpp` / `.h` - Native bridge registry
* `EmbeddedScripts.h` - Virtual file system wrapper for embedded arrays
* `main.nd` - Entry NetDust script
* `io.nd` - Standard I/O module script

---

## 2. Build Instructions

Run the following commands in your terminal from the root directory of your project:

> [!NOTE]
> - **Step 1** converts your `.nd` script files into standard C-style byte array header files (`.h`).
> - **Step 2** compiles the C++ sources and embedded scripts into a single standalone executable named `nd-cli`.

```bash
# Step 1: Convert NetDust scripts into C byte array headers
xxd -i main.nd > main_nd.h
xxd -i io.nd > io_nd.h

# Step 2: Compile the standalone native executable
g++ -std=c++17 -O2 main.cpp NetDustInterpreter.cpp NativeLibraryRegistry.cpp -o ndr
```

## 3. Running the Application

Once compiled, you can execute the generated binary directly. 
It runs independently without needing external `.nd` files or background runtime environments:

```bash
# Execute the standalone binary
./ndr-cli

# Run with runtime debug tracing enabled
./nd-cli --debug
```
