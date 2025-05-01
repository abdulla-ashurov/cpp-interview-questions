# Juniour

## C Language

### 1. How does static affect global/local variables?

`Static` with Global Variables: a global variable declared with `static` limits its scope to the file where it is declared. A global `static` variable is allocated in the data segment at compile-time and is initialized before `main()` starts, during program startup phase.

- Without `static`: A global variable is externally visible and can be accessed from other files using `extern`.
- With `static`: The global variable is restricted to the current file, making it private to that file (also known as internal linkage).

`Static` with Local Variables: a local variable declared with static retains its value across function calls

- Without `static`: The variable is created and destroyed every  time the function is called.
- With `static`: The variable persists throughout the program's execution but remains local to the function.

### 2. How does const affect a variable?

The `const` keyword in C++ makes a variable **read-only**, meaning its value cannot be modifed after initialization.

### 3. What are the uses of extern?

The `extern` keyword is use to declare variables or functions that are defined in another translation unit (source file). It helps in linking global variables and function across multiple files.

Common Uses of `extern`:

- Accessing Global Variables from Another file:

    ```cpp
    // file1.cpp
    #include <iostream>
    int globalVar = 42;  // Global variable definition
    ```

    ```cpp
    // file2.cpp
    #include <iostream>
    extern int globalVar;  // Declaration (no memory allocation)
    int main() {
        std::cout << globalVar << std::endl;  // Prints 42
        return 0;
    }
    ```

- Declaring a Function from Another File: If a function is defined in one file, we can use extern to access it in another file:

    ```cpp
    // file1.cpp
    #include <iostream>
    void sayHello() {
        std::cout << "Hello, World!" << std::endl;
    }
    ```

    ```cpp
    // file2.cpp
    extern void sayHello();  // Declaration
    int main() {
        sayHello();  // ✅ Works fine
        return 0;
    }
    ```

- Using `extern` with `const` Variables: By default, `const` variables have internal linkage (they are not visible outside the file). To use a `const` variable across files, we must declare it with `extern`. Without `extern`, `MAX_VALUE` would have file scope and could not be accessed in `file1.cpp`.:

    ```cpp
    // file1.cpp
    #include <iostream>
    extern const int MAX_VALUE;  // Declaration (does not allocate memory)
    void printMax() {
        std::cout << MAX_VALUE << std::endl;
    }
    ```

    ```cpp
    // file2.cpp
    #include <iostream>
    const int MAX_VALUE = 100;  // Definition
    int main() {
        printMax();  // Prints 100
        return 0;
    }
    ```

- Using `extern "C"` for C++ and C Compatibility: When working with C and C++ together, `extern "C"` is used to prevent C++ name mangling, allowing C++ to call C functions.

    ```cpp
    // file1.c (C file)
    #include <stdio.h>
    void cFunction() {
        printf("This is a C function\n");
    }
    ```

    ```cpp
    // file2.cpp (C++ file)
    extern "C" void cFunction();  // Prevents name mangling
    int main() {
        cFunction();  // Works fine
        return 0;
    }
    ```

### 4. What are the uses of volatile?

The `volatile` keyword in C++ is used to indicate that a variable can be changed at any time by external factors (such as hardware, other thread, or interrupt routines) and should not be optimzed by the compiler.

What `volatile` Does NOT Do:

- It does not make code thread-safe (use `std::atomic` for that).
- It does not prevent race conditions.

### 5. What are the bitwise operations?

Bitwise operations allow direct manipulation of bits. They are commonly used in low-level programming, such as encryption, compression, embedded systems, and performance optimizations.

### 6. Tell us about the stages of developing a library or program

1. Requirements Analysis
2. Planning & Desing
3. Implementing
4. Testing & Debugging
5. Documentation
6. Compilation & Build Process
7. Deployment & Distribution
8. Maintence & Updates

### 7. What are sorting algorithms and which ones do you know?

Sorting algorithms are used to arrange data in a specific order (ascending or descending). They are widely used in searching, data processing, and optimizing algorithms.

Some well-known sorting algorithms include:

- Buble Sort - Simple but inefficient (O(n²)).
- Selecting Sort - Finds the smallest element and swaps (O(n²))
- Insertion Sort - Builds the sorted array one element at time (O(n²))
- Merge Sort - Uses the divide and conquer approach (O(n log n))
- Quick Sort - Uses a pivot and partitioning technique (O(n log n))
- Heap Sort - Uses a binary heap to extract the min/max (O(n log n))
- Radix Sort - Sorts number digit by digit (O(nk))
- Bucket Sort - Divides elements into buckets and sorts them (O(n + k))

### 9. What are the graph algorithms?

Graph algorithms are used to solve problems related to graphs, which are data structures consisting of vertices (nodes) and edges (connections between nodes). These algorithms help in searching, traversing, shortest path finding, cycle detection, and more.

### 10. Where can a variable be stored?

A variable in C++ can be stored in the following memory regions:

- `Stack` - stores local variables and function call information. Memory is allocated and deallocated automatically (LIFO structure).
- `Heap` - stores dynamically allocated variables (`new` in C++). Memory must be managed manually (`delete`).
- `Data Segment (Static/Global Memory)` - Stores `global` and `static` variables, divided into:
  - `Initialized Data Segment` - Stores `global/static` variables an initial value.
  - `Uninitialized (BSS) Segment` - Stores `global/static` variables without an initial value.
- `Code Segment (Text Segment)` - Stores executable program instructions.

### 11. What is realloc used for?

`realloc` is used to resize previously allocated heap memory. It adjusts the size of a memory block allocated by malloc or realloc while preserving its contents. If the new size is larger, additional space is allocated. If it is smaller, excess memory may be freed.

### 12. What is a pointer?

A pointer is a variable that stores the memory address of another variable. Instead of holding a direct value, it holds the location where a value is stored in memory.

Types of Pointers:

- Null Pointer (nullptr) - a pointer that does not point to any valid memeory.
- Void Pointer (void*) - a generic pointer that can store addresses of any data type.
- Function pointer - stores the address of a function.
- Constant pointer - a pointer that cannot change its address
- Pointer to pointer - a pointer storing the address of another pointer.

### 13. What is the size of a pointer and what does it depend on?

The size of a pointer depends on the architecture of the system and the memory model being used:

- On a 32-bit system, a pointer is 4 bytes (32 bits).
- On a 64-bit system, a pointer is 8 bytes (64 bits).

### 14. What are the pointer operations?

Pointers allows us to manipulate memory addresses. The key operations that can be performed on pointers include:

- Assignment (=)
- Deferencing (*)
- Address-of (&)
- Pointer arithmetic (++, --, +, -)
- Comparison (==, !=, >, <)

### 15. What is a struct?

A struct (short for "structure") is a user-defined data type in C++ that allows us to group different types of data together under a single name. This is useful when you need to store multiple related pieces of information.

- Members of a struct: A struct can contain variables (called members or fields) of different types, such as integers, floats, characters, etc.
- Default access specifier: By default, the members of a struct are public, meaning they can be accessed directly from outside the struct. If you want members to be private or protected, you have to specify that explicitly using private or protected.

Key Points:

- Access to members: Members of a struct are public by default, so they can be accessed directly. For example, p1.name can be accessed directly.
- Size of an empty struct: If a struct is empty, it will still have a size of 1 byte. This is due to the fact that the compiler needs to reserve space for the struct's internal bookkeeping. Even though the struct doesn't contain any data, it cannot have a size of 0 because memory allocation rules prevent it.

### 16. How to determine the size of structures?

The size of a structure in C++ depends on the size of its members, the alignment requirements, and potential padding (used to align the data to specific boundaries for performance optimization).

### 17. What is alignment in structures?

Alignment in structures refers to the practice of arranging data members of a structure in memory such that they conform to the alignment requirements of the data types. This ensures that each member of the structure is placed in memory in a way that respects the memory boundaries, which leads to more efficient memory access.

### 18. What is union?

A union in C and C++ is a special data structure that allows multiple members to share the same memory location. It enables storing different data types in the same memory space, but only one member of the union can hold a value at any given time. A union helps save memory by allowing different variables to use the same space, but at the cost of not being able to store values in multiple members simultaneously.

Key Features of a Union:

- Memory Sharing: All members of a union share the same memory location. The size of a union is determined by the size of its largest member because the union must be large enough to store the largest data type.
- One Active Member: Only one member of the union can hold a value at any given time. When a new value is assigned to one member, it overwrites the value of the other members.
- Memory Efficiency: Unions help conserve memory when you need to store different types of data but do not need to use them simultaneously.
