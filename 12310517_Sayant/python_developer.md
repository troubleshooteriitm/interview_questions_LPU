
## 1. Explain how Python memory management works.

Python manages memory automatically using: - **Private Heap:** All
Python objects are stored in a private heap managed by the Python memory
manager. - **Reference Counting:** Every object keeps track of how many
references point to it. When the count reaches zero, the object is
deallocated. - **Garbage Collection:** Python's `gc` module detects and
removes cyclic references that reference counting alone cannot free. -
**Memory Allocator (pymalloc):** CPython uses `pymalloc` to efficiently
allocate memory for small objects.

------------------------------------------------------------------------

## 2. What is the Global Interpreter Lock (GIL)?

The **Global Interpreter Lock (GIL)** is a mutex in CPython that allows
only **one thread to execute Python bytecode at a time**, even on
multi-core processors.

**Advantages** - Simpler memory management. - Prevents race conditions
in CPython's object model.

**Disadvantages** - CPU-bound multithreaded programs cannot fully
utilize multiple CPU cores.

------------------------------------------------------------------------

## 3. When does the GIL become a bottleneck?

The GIL becomes a bottleneck for **CPU-bound** multithreaded
applications, where multiple threads compete to execute Python bytecode.

Examples: - Image processing - Scientific computation - Large
mathematical calculations

For **I/O-bound** tasks (network requests, file operations, databases),
threads often release the GIL while waiting, so threading remains
effective.

------------------------------------------------------------------------

## 4. Difference between multiprocessing, threading, and asyncio.

  -------------------------------------------------------------------------
  Feature       Threading         Multiprocessing           asyncio
  ------------- ----------------- ------------------------- ---------------
  Workers       Threads           Processes                 Coroutines

  Memory        Shared            Separate                  Shared

  GIL Affected  Yes               No                        Single thread

  Best For      I/O-bound tasks   CPU-bound tasks           Massive
                                                            concurrent I/O

  True          No (CPython)      Yes                       No
  Parallelism                                               
  -------------------------------------------------------------------------

**Use threading** for file or network I/O.

**Use multiprocessing** for heavy CPU computations.

**Use asyncio** when handling thousands of concurrent I/O operations
efficiently.

------------------------------------------------------------------------

## 5. How does Python import work?

When Python imports a module:

1.  It checks whether the module is already loaded in `sys.modules`.
2.  If not found, it searches the directories listed in `sys.path`.
3.  The module is compiled to bytecode if necessary.
4.  The module executes once.
5.  The loaded module is cached in `sys.modules`, so future imports
    reuse it.

------------------------------------------------------------------------

## 6. Explain `__new__` vs `__init__`.

  -----------------------------------------------------------------------
  `__new__`                         `__init__`
  --------------------------------- -------------------------------------
  Creates the object                Initializes the object

  Runs first                        Runs after `__new__`

  Returns the instance              Returns `None`

  Used mainly for immutable objects Used to initialize attributes
  or custom object creation         
  -----------------------------------------------------------------------

Example:

``` python
class Demo:
    def __new__(cls):
        print("Creating object")
        return super().__new__(cls)

    def __init__(self):
        print("Initializing object")
```

Output:

    Creating object
    Initializing object

------------------------------------------------------------------------

## 7. Explain descriptors.

A **descriptor** is any object that defines one or more of these
methods:

-   `__get__`
-   `__set__`
-   `__delete__`

Descriptors customize attribute access and are the mechanism behind: -
`property` - Methods - `classmethod` - `staticmethod`

Example:

``` python
class Positive:
    def __get__(self, instance, owner):
        return instance._value

    def __set__(self, instance, value):
        if value < 0:
            raise ValueError("Must be positive")
        instance._value = value
```

Descriptors are commonly used for validation, computed attributes, and
reusable attribute behavior.

------------------------------------------------------------------------

## 8. Explain metaclasses.

A **metaclass** is the class of a class. Just as classes create objects,
metaclasses create classes.

By default, Python uses the built-in `type` metaclass.

Metaclasses let you: - Modify a class before it is created. -
Automatically add methods or attributes. - Enforce coding standards. -
Build frameworks (e.g., Django ORM).

Example:

``` python
class MyMeta(type):
    def __new__(cls, name, bases, attrs):
        attrs["company"] = "OpenAI"
        return super().__new__(cls, name, bases, attrs)

class Employee(metaclass=MyMeta):
    pass

print(Employee.company)
```

Output:

    OpenAI

Metaclasses are an advanced feature and are most often used in framework
development rather than everyday application code.
