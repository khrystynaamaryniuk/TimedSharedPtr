# Architecture Overview

## Design Pattern

TimedSharedPtr implements a hybrid approach combining:
- **Shared Ownership**: Multiple pointers can own the same object
- **Reference Counting**: Automatic cleanup when all references are released
- **Time-Based Expiration**: Objects expire after a configurable duration

## Core Components

### TimedSharedPtr\<T\> (Public Interface)

Templated smart pointer class providing:
- Copy constructor and assignment operator for reference sharing
- Pointer operators (`*`, `->`) for transparent object access
- `get()` method returning pointer or `nullptr` if expired
- `use_count()` method reporting active reference count
- `resetTimer()` method extending object lifetime

### ControlSharedPtr\<T\> (Control Block)

Internal structure managing:
- **ptr**: Raw pointer to managed object
- **myUseCount**: Reference counter
- **startTime**: Clock snapshot at creation
- **deleteInMs**: Expiration threshold in milliseconds

## Reference Flow

1. **Creation**: `TimedSharedPtr<T>(raw_ptr, ms)` creates `ControlSharedPtr` with count=1
2. **Copy**: Copy constructor increments count
3. **Assignment**: Assignment operator updates reference and adjusts counts
4. **Destruction**: Destructor decrements count; deletes `ControlSharedPtr` when count reaches 0
5. **Cleanup**: `ControlSharedPtr` destructor deletes managed object

## Expiration Logic

- Timer starts at `ControlSharedPtr` creation
- On each `get()` call, elapsed time is compared against `deleteInMs`
- If expired, method returns `nullptr` (no automatic deletion)
- Timer can be reset via `resetTimer()` to extend lifetime
