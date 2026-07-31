
## 1. Explain how Python memory management works.

**Answer:** Python manages memory automatically using reference counting
and a garbage collector. Objects are created on the heap, and memory is
freed when objects are no longer referenced. The garbage collector also
removes cyclic references.

## 2. What is the Global Interpreter Lock (GIL)?

**Answer:** The GIL is a mutex in CPython that allows only one thread to
execute Python bytecode at a time, ensuring thread safety for Python
objects.

## 3. When does the GIL become a bottleneck?

**Answer:** The GIL becomes a bottleneck in CPU-bound multithreaded
programs because only one thread can execute Python bytecode at a time.
It is less of an issue for I/O-bound tasks.

## 4. Difference between multiprocessing, threading, and asyncio.

**Answer:** - **Multiprocessing:** Uses multiple processes; suitable for
CPU-bound tasks. - **Threading:** Uses multiple threads in one process;
suitable for I/O-bound tasks. - **Asyncio:** Uses a single-threaded
event loop with coroutines for many concurrent I/O operations.

## 5. Explain generators and `yield`.

**Answer:** A generator is a function that returns values one at a time
using the `yield` keyword instead of returning all values at once,
making it memory efficient.

## 6. Generator vs Iterator.

**Answer:** - **Generator:** Automatically created using a function with
`yield`. - **Iterator:** Any object implementing `__iter__()` and
`__next__()` methods. - All generators are iterators, but not all
iterators are generators.

## 7. How do decorators work internally?

**Answer:** A decorator is a function that takes another function as
input, adds extra functionality, and returns a new function without
modifying the original function.

## 8. Explain closures.

**Answer:** A closure is an inner function that remembers and can access
variables from its enclosing function even after the outer function has
finished executing.

## 9. Explain monkey patching.

**Answer:** Monkey patching is the practice of modifying or replacing
classes, methods, or functions at runtime without changing the original
source code.

## 10. Mutable vs Immutable objects.

**Answer:** - **Mutable:** Objects whose contents can be changed after
creation (e.g., list, dict, set). - **Immutable:** Objects whose
contents cannot be changed after creation (e.g., int, float, string,
tuple).
