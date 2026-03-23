# Build & Setup Guide

## Requirements

- **C++ Compiler**: g++ or clang with C++17 support
- **OS**: macOS, Linux, or Windows (with g++)
- **Build Tool**: g++ (no additional build system required)

## Build Commands

**Compile Main Program:**
```bash
g++ -std=c++17 -o timed_ptr start.cpp
```

**Compile Unit Tests:**
```bash
g++ -std=c++11 -I. -o unit_testing unit_testing.cpp
```

**Run Main Program:**
```bash
./timed_ptr
```

**Run Unit Tests:**
```bash
./unit_testing
```

## Project Structure

```
.
├── start.cpp              # Main program with interactive examples
├── unit_testing.cpp       # Unit tests for TimedSharedPtr
├── TimedSharedPtr.h       # Public API template class
├── ControlSharedPtr.h     # Internal control block (reference counting & timing)
├── doctest.h              # Testing framework (header-only)
├── README.md              # Project overview
└── SETUP.md               # This file
```

## Key Classes

- **TimedSharedPtr\<T\>**: Template class providing timed shared pointer interface
- **ControlSharedPtr\<T\>**: Internal structure managing reference count and expiration logic
