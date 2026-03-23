# Changelog

## Version 1.0.0 (Final Release)

### Features
- Full `TimedSharedPtr<T>` template implementation with time-based expiration
- Reference counting control block (`ControlSharedPtr<T>`)
- Support for custom expiration times with millisecond precision
- Complete operator overloading (`*`, `->`, `=`)
- Timer reset functionality to extend object lifetime

### Implementation
- Comprehensive unit tests using doctest framework
- Interactive demo program with multiple usage examples
- Support for C++17 and C++11 compilation
- High-resolution timer using `std::chrono`

### Documentation
- README with quick start and feature overview
- Build and setup guide (SETUP.md)
- Architecture documentation explaining design patterns
- Inline code comments for complex logic
