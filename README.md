# TimedSharedPtr

A custom C++ implementation of a shared pointer with automatic expiration and cleanup. Combines reference counting with time-based memory management for automatic resource deallocation.

## Features

- **Reference Counting**: Tracks multiple owners of the same object
- **Time-Based Expiration**: Automatic pointer expiration after a specified duration
- **Timer Reset**: Extend object lifetime by resetting expiration timer
- **Smart Cleanup**: Safely deletes objects when all references are released or timeout occurs
- **Operator Overloading**: Implements `*`, `->`, and assignment operators for intuitive usage
- **Comprehensive Testing**: Full unit test suite with doctest framework

## Tech Stack

- **Language**: C++17 (C++11 for unit tests)
- **Testing**: doctest header-only framework
- **Timing**: `std::chrono` for high-resolution clock operations

## Getting Started

```bash
git clone https://github.com/khrystynaamaryniuk/CSE3150_Final.git
cd CSE3150_Final
g++ -std=c++17 -o timed_ptr start.cpp
./timed_ptr
```

## How It Works

1. **Create**: Instantiate `TimedSharedPtr` with a raw pointer and optional expiration time (default: 1000ms)
2. **Share**: Copy constructor and assignment operator manage reference counts
3. **Monitor**: Query `use_count()` to see how many references exist
4. **Access**: Use `.get()`, `*`, or `->` operators to access the managed object
5. **Expire**: Object automatically returns `nullptr` when expiration time elapses

## Architecture

- **TimedSharedPtr**: Public interface for creating and managing timed pointers
- **ControlSharedPtr**: Internal control block storing reference count, pointer, and timer state
- **Reference Counting**: Maintains count of active references for safe deletion
- **Time Tracking**: Captures creation time and compares against deletion threshold on each access

## Dependencies

- C++17 standard library (`chrono`, `iostream`, `thread`)
- doctest.h (header-only unit testing framework, included)