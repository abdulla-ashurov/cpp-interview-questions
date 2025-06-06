# Juniour

## Genaral questions

### 1. What are the basic principles of OOP?

- `Encapsulation` - The bundling of data (variables) and methods (functions) that operate on the data into a single unit (class) while restricting direct access to some details. This is typically achieved using access specifiers like `private`, `protected`, and `public`. Encapsulation helps in data hiding and enforcing modular design.

- `Inheritance` - A mechanism where one class (child/derived class) inherits attributes and behaviours (methods) from another class (parent/base class). This promotes code reusability and establishes a relationship between classes (e.g., `class Dog : public Animal{}` means `Dog` inherits from `Animal`).

- `Polymorphism` - The ability of different classes to be treated as instances of the same class through a common interface. This allows methods with the same name to behave differently based on the object they operate on. It is achieved via:
  - `Compile-time (Static) Polymorphism` - Achieved using function overloading and operator overloading.
  - `Run-time (Dynamic) Polymorphism` - Achieved using method overriding with virtual functions and dynamic dispatch.

- `Abstraction` - Hiding implementation details and exposing only the necessary functionaly. THis is often achieved through abstract classes and interfaces (pure virtual functions in C++).

### 2. What is the algorithm complexity?

Algorithm complexity refers to the measurement of how an algorithm's resource consumption grows relative to the input size. It is primarily analyzed in terms of:

**Time Complexity** – Describes how the execution time of an algorithm increases as the input size grows. It is commonly expressed using `Big-O` notation, which represents the upper bound of the growth rate (e.g., `O(1)`, `O(log N)`, `O(N)`, `O(N²)`, etc.).

**Space Complexity** – Describes the amount of memory an algorithm requires as the input size grows. It includes both the auxiliary space used by the algorithm and the input storage itself.

`Big-O` notation provides an abstract way to describe the worst-case or upper-bound growth rate of an algorithm. Some common complexities are:

- `O(1)` – Constant Time: Execution time remains the same regardless of input size (e.g., accessing an array element by index).
- `O(log N)` – Logarithmic Time: Execution time grows logarithmically, often seen in divide-and-conquer algorithms (e.g., binary search).
- `O(N)` – Linear Time: Execution time grows proportionally with input size (e.g., iterating over an array).
- `O(N²)` – Quadratic Time: Execution time grows quadratically, often seen in nested loops (e.g., bubble sort).
`- O(2ⁿ)` – Exponential Time: Execution time doubles with each additional input size (e.g., recursive Fibonacci without memoization).

### 3. Explain such data structures as stack and queue

`Stack` is a linear data structure that follow the `LIFO` (**Last In, First Out**) principle. The last element added (pushed) to the stack is the first on to be removed (popped). It is typically implemented using arrays or linked lists.

Common operations:

- `push(value)` - adds an element to the top of the stack.
- `pop()` - removes the top element of the stack.
- top() - returns the top element without removing it.
- `empty()` - checks if the stack is empty.

Example use cases:

- Functions call stack in programming (recursion).
- Unde/Redo functionality in text editors.
- Backtracking algorithms (Depth-First-Search).

`Queue` is a linear data structure that follows the `FIFO` (**First In, First Out**) principle. The first element added to the queue is the first one to be removed.

Common operations:

- `push(value)` - adds an element to the back of the queue.
- `pop()` - removes the front element of the queue.
- `front()` - returns the front element of the queue.
- `empty()` - checks if the queue is empty.

Example use cases:

- Task scheduling (CPU scheduling, printer queue).
- Breadth-First-Search in graphs.
- Handling request in web servers.

### 4. What interesting things have you found in the new standarts C++17, C++20?

C++17 and C++20 introduced several useful features that improve performance, code readability, and developer productivity.

C++17 Highlights:

- `std::optional` - a wrapper that represents and optional value (usufel for returning "no value" withour using `nullptr` or special values).

    ```cpp
    std::optional<int> maybeValue = std::nullopt;
    ```

- `std::variant` - a type-safe alternative to `union`, allowing multiple types in a single variable.
- `std::any` - a type-safe container that can hold any type.
- Structured Bindings - allows unpacking tuples, pairs and structs.

    ```cpp
    auto [x, y] = std::make_pair(10, 20);
    ```

- `if constexpr` - enables compile-time branching for template metaprogramming.
- Filesystem Library (`<filesystem>`) - provides tools for file operations like copying, deleting, and navigating directories.
- `Parallel Algorithms` - standard algorithms like `std::sort` can now run in parallel.

C++20 Highlights:

- Concepts - adds constraints to templates, improving error messages and clarity.

    ```cpp
    template <typename T>
    requires std::integral<T>
    void func(T value) {}
    ```

- Ranges Library - simplifies working with collections and algorithms.
- Coroutines - enables writing asynchrouns code with `co_await`, `co_yield` and `co_return`.
- `std::span` - provides a non-owning view over contiguous data (like arrays).
- Modules - replaces headers with a more efficient and scalable way to manage dependencies.
- Three-Way Comprasion (`<=>`) - simplifies comparison operator overloading.
- Calender & Time Zones (`<chrone>`) - improves data/time managament.

### 5. What is the ASCII table?

The ASCII (American Standard Code for Information Interchange) table is a character encoding standard that assigns a unique numerical value to characters, including letters, digits, punctuation, and control characters.

- Size: ASCII uses 7 bits to represent characters, allowing 128 unique values (0-127). Homever, it is often stored in 1 byte (8 bits), with the extra bit sometimes used for error checking or extended character sets.
- Structure:
  - `0-31`: Control characters (e.g., `\n` (newline), `\t` (tab), `\0` (null)).
  - `32-126`: Printable characters (letters, numbers, symbols).
  - `127`: DEL (delete) character
- Extended ASCII: Some systems use 8-bit ASCII (0-255), which includes additional special and international characters.

### 6. What is Unicode?

Unicode is a universal character standard designed to represent characters from all writing systems, symbols, and emojis in a consistent manner acrross different platforms and languages.

- Why Unicode?
    ASCII is limited to 128 characters, whule Unicode supports over 1.1 million character, covering languages like Chinese, Arabic, and special symbols.
- Popular Unicode Encoding Standards:

  - UTF-8 (Variable-length: 1-4 bytes per character)
  - Most commonly used (in web pages, URLs, Linux systems)
  - Backward compatible with ASCII (first 128 characters are the same)
- UTF-16 (Variable-length, 2 or 4 bytes per character)
  - Used in Windows, Java, ans some file formats.
- UTF-32 (Fixed-length, 4 bytes per character)
  - Uses more memory but provides direct indexing of characters.

### 7. What are unit tests for?

Unit tests are automated tests that verify the correctness of individual components (or "units") of a program, typically at the function or class level. The goal of unit testing is to ensure that each unit of the software behaves as expected in isolation.

Key Features of Unit Tests:

- Small Scope: Tests only a single function, method or class.
- Automation: Executed automatically using testing frameworks.
- Isolation: Should not depend on external systems (e.g., databases, APIs).

Why Use Unit Tests?

- Ensure correctness - catch bugs early in development.
- Improve code maintainability - refactor code with confidence.
- Speed up development - quickly detect errors before integration.
- Prevent regressions - ensure that changes do not break existing functionaly.

### 8. What is difference between unit and intergration tests?

- **Unit Tests** ensure that individual functions/classes work correctly in isolation.
- **Integration Tests** check if multiple components (e.g., database, API work together properly).

**Testing Freworks**: GoogleTest, Catch2, Boost.Test.

### 9. What is TDD?

**Test-Driven Development (TDD)** is a software development approach where tests are written before the actual implementation. It follows a strict cycle:

**TDD Cycle (Red-Green-Refactor)**:

- **Red** - Write a failing test (since the functionality does not exist yet).
- **Green** - Implement the minimum code required to pass the test.
- **Refactor** - Improve the code while ensuring the test still passes.

**Benifits of TDD**:

- Ensures high code quality from the start
- Reduces bugs and makes code easier to maintain
- Encourages writing modular and testable code
- Increases developer confidence in making changes

## Metaprogramming

### 1. What is a template class and a template function?

Templates in C++ allow writing **generic code** that works with different data types. They help **reduce code duplication** by enabling functions and classes to handle multiple data types without rewriting the same logic.

**Template Function** is a function that works with any data type, determined at **compile-time**.

**Template Class** allows defining a class that operates on any data type.

**Advantages of Templates**:

- Reduces Code Duplication - no need to write separate versions for different types.
- Type-Safe - the compiler ensures type correctness at compile-time.
- More Generic and Reusable - the same logic can be use for multiple types.

### 2. What are constructores? What types do you know?

A constructor is a special member function of a class that is automatically called when an object of the class is created. It initializes the object's data members.

**Types of Constructors**:

- **Defaut Constructor** - a constructor that takes no arguments and initialize an object with default values.
- **Parameterized Constructor** - a constructor that takes arguments to initialize an object with specific values.
- **Copy Constructor** - a constructor that creates a new object as a copy of an existing object. It is called when passing an object by value or returning an object by value.
- **Move Constructor (C++11)** - a constructor that moves resources from a temporary (rvalue) object instead of copying them, improving performance.

**Other types of Constructors**:

- **Explicit constructor** - prevents implicit conversion by using `explicit`.
- **Delegating Constructor (C++11)** - a constructor that calls another constructor in the same class.

### 3. Can a constructor be a template function?

Yes, a constructor in C++ can be a template function. This allows a class to have a constructor that works with different types without making the entire class a template.

**When to Use a Template Constructor?**

- When you want flexible object creation without making the entire class a template.
- When the class itself doesn’t depend on a type, but the constructor does.

### 4. Can a virtual function be a template function?

No, a virtual function cannot be a template function in C++.

Why Not?

- **Virtual functions rely on dynamic dispatch (VTable mechanism)** - they are resolved at runtime based on the actual type of the object.
- **Templates rely on compile-time instantiation** - template functions are generated during compilation for each specific type used.

Since virtual functions require a fixed function signature in the VTable, they cannot be templated, as templates generate different versions for different types at compile-time.

**What is the Alternative?**

If you need template-like behaviour with polymorphism, you can use non-template virtual functions in combinations with templated base classes or **CRTP** (**Curiously Recurring Template Pattern**).

**What If You Need a Template-Like Virtual Function?**

A workaround is the use Curiously Recurring Template Pattern (CRTP):

```cpp
#include <iostream>

template <typename Derived>
class Base {
public:
    void print() const {  // Calls the derived class method
        static_cast<const Derived*>(this)->printImpl();
    }
};

class DerivedInt : public Base<DerivedInt> {
public:
    void printImpl() const {
        std::cout << "DerivedInt implementation" << std::endl;
    }
};

class DerivedString : public Base<DerivedString> {
public:
    void printImpl() const {
        std::cout << "DerivedString implementation" << std::endl;
    }
};

int main() {
    DerivedInt obj1;
    DerivedString obj2;

    obj1.print();  // Output: DerivedInt implementation
    obj2.print();  // Output: DerivedString implementation

    return 0;
}
```

### 5. What is template instantiation?

Template instantiation is the process where the compiler generates concreate function or class definitions from a template based on the provided type(s).

C++ templates are note compiled directly. Instead, they act as blueprints, and actual code is generated when they are instantiated with specific types.

**Types of Template Instantiation**:

- Implicit Instantiation (Done automatically by the compiler when needed)

```cpp
#include <iostream>

// Function Template
template <typename T>
T square(T x) {
    return x * x;
}

int main() {
    int a = square(5);     // Compiler creates square<int>(int)
    double b = square(3.5); // Compiler creates square<double>(double)
    
    std::cout << a << " " << b << std::endl;  // Output: 25 12.25
}
```

- Explicit Instantiation (Manually specified by the programmer)

```cpp
template class std::vector<int>;  // Forces instantiation of vector<int> in this file
```

- Explicit specialization (Custome implementation for a specific type)

```cpp
#include <iostream>

template <typename T>
class Printer {
public:
    void print(T value) {
        std::cout << "General template: " << value << std::endl;
    }
};

// Specialization for char*
template <>
class Printer<char*> {
public:
    void print(char* value) {
        std::cout << "Specialized for char*: " << value << std::endl;
    }
};

int main() {
    Printer<int> p1;
    p1.print(42);  // General template

    Printer<char*> p2;
    p2.print("Hello");  // Specialized version

    return 0;
}
```

### 6. What is template specialization? Partial template specialization?

Template specialization allows to define a custom implementation for a specific type or set of types when usig a template. Instead of relying on the general template logic, you can provide a specialized version of the template that is used when the template is instantiated with a particular type.

Full specialization means defining a specific version of a template for one exact type:

```cpp
#include <iostream>

// General template
template <typename T>
class Printer {
public:
    void print(T value) {
        std::cout << "General template: " << value << std::endl;
    }
};

// Full specialization for char* type
template <>
class Printer<char*> {
public:
    void print(char* value) {
        std::cout << "Specialized for char*: " << value << std::endl;
    }
};

int main() {
    Printer<int> p1;
    p1.print(42);  // General template

    Printer<char*> p2;
    p2.print("Hello");  // Specialized version

    return 0;
}
```

Partial specialization allows to provide a specialized version of the template for a certain subset of types that match specific criteria, while still keeping the general template for others.

```cpp
#include <iostream>

// General template
template <typename T, typename U>
class Pair {
public:
    T first;
    U second;
    
    Pair(T first, U second) : first(first), second(second) {}
    
    void print() {
        std::cout << "General Pair: " << first << ", " << second << std::endl;
    }
};

// Partial specialization for when both types are the same
template <typename T>
class Pair<T, T> {  // Specialization for Pair<T, T> (same types)
public:
    T first;
    T second;
    
    Pair(T first, T second) : first(first), second(second) {}
    
    void print() {
        std::cout << "Specialized Pair (same types): " << first << ", " << second << std::endl;
    }
};

int main() {
    Pair<int, double> p1(1, 3.5);  // Uses general template
    Pair<int, int> p2(2, 2);       // Uses partial specialization
    
    p1.print();  // Output: General Pair: 1, 3.5
    p2.print();  // Output: Specialized Pair (same types): 2, 2
    
    return 0;
}
```

### 7. Tell us about implementing template classes in a cpp file?

Implementing template classes in a .cpp file requires a slightly different approach than implementing regular non-template classes because templates are instantiated at compile time and must be available to the compiler in the header file (or at least in the translation unit where they are used).

**Why Can't Template Class Definitions Be in a `cpp` File?**

Templates are **compile-time constructs**, meaning the actual code is generated when you instantiate a template with a specific type. The defition of the template must be visible to all translation units that use it, so you can't just define template classes in a `.cpp` file.

To manage this, template class definitions are usually included in `header files` (`.h` or `.hpp`). However, you can still define template member functions in a separate `.cpp` file using explicit instantiation.

## Preprocessor and Compilation

### 1. How does the process of compiling cpp files into a binary file work?

- Preprocessing:

  - The preprocesser handles all the `#include` directives, `#define` macros, and confitional compilation instructions: `#ifdef`, `ifndef`, `#endif`.
  - It generates a `predprocessed` source file where all the macros and headers are expanded. This stage ensures that all the external dependencies (like header files) are included in the source code.

- Compilation:
  - The compiler takes the processed source code (the `cpp` file) and translated it into assembly language.
  - In this stage:
    - Syntax checks are performed.
    - Semantics checks are done (e.g., type checking).
    - The intermediate object code is generated for each source file, which contains machine-level instructions but still lacks full program context (i.e., it cannot run yet).

- Assembly:

  - The assembler converts the assembly code generated by the compiler into binary machine code.
  - The machine code is specific to the platform on wher it is compiling
  - The result of this step is an object file (with `.o`, or `.obj` extensions).

- Linking:

  - The linker is responsible for combining one or more object files into a single executable.
  - It resolves symbol references (such as functions or variables) that are used across multiple files.

    - If one object file references a function from another object file, the linker will make sure that reference is correctly resolved.
  - The linker also handles library linking. If your code depends on external libraries (like `libstdc++` for the standard library), the linker will include the necessary code from those libraries.
  - The output of this step is an executable binary file (e.g., `.exe` on Windows, or simply an executable on Linux/macOS).

### 2. What is a preprocessor and how does a preprocessor work?

The preprocessor is a tool that processes source code before the actual compilation begins. It handles various operations like including header files, defining macros, and setting up conditional compilation. The preprocessor commands are processed during the preprocessing step, which occurs before the compilation stage in the build process.

### 3. What preprocessor commands do you know?

- Including Header Files:

  - The preprocessor handles `#include` directives, which allow the inclusion of external header files into the source code.
  - This helps avoid code duplication and makes it easier to manage and reuse code (e.g., including standard libraries or custom header files).

  ```cpp
  #include <iostream> // Includes the standard library header for input/output
  ```

- Defining Macros:

  - The preprocessor processes `#define` directives to define constants or macros, which can be used throughout the program.
  - Macros are replaced by the preprocessor with their corresponding values before the code is compiled.

  ```cpp
  #define PI 3.14159 // Defines a macro named PI
  ```

- Conditional Compilation:

  - The preprocessor can conditionally include or exclude parts of code using directives like `#ifdef`, `#ifndef`, and `#endif`. This is helpful for platform-specific code or debugging.

  ```cpp
  #ifdef DEBUG
  std::cout << "Debugging mode\n";
  #endif
  ```

- Guarding Header Files:

  - One of the most important uses of the preprocessor is to prevent multiple inclusins of the same header file using include guard.
  - This ensures that a header file is only included once per compilatio, avoiding potential errors from multiple definitions.

  ```cpp
  #ifndef MY_HEADER_H
  #define MY_HEADER_H

  // Header file content here

  #endif
  ```

### 4. What exactly does the linker link?

The linker is responsible for combining multiple object files (produced by the compiler) into a single executable. It also resolves any references to functions or variables between different object files. Here’s a breakdown of what the linker links:

- Object Files:

  - The linker combines object files (`.o` or `.obj`) generated by the compiler into an executable. These object files contain machine code that is not yet fully connected.
  - It resolves references between object files, so if one file refers to a function or variable defined in another, the linker will establish those connections.

- External Libraries:

  - The linker also links external libraries (e.g., standard C++ libraries or third-party libraries).
  - If you are using a library like `libstdc++`, the linker will include the necessary parts of this library into the final executable.

- Symbols and Addresses:

  - The linker resolves symbol references (e.g., function calls, variable access) across the object files. It ensures that when a function is called, it is correctly linked to the function's address in memory.
  - This process is also known as symbol resoution.

- Static and Dynamic Linking:

  - Static Linking: In this case, the linker copies all the necessary code from libraries directly into the executable at compile time.
  - Dynamic Linking: The linker doesn’t include the code from shared libraries directly but instead links to the library at runtime. This allows multiple programs to share the same library, saving memory.

- Relocation:

  - If the object code has addresses that need to be adjusted (e.g., variables or function addresses), the linker performs relocation, which modifies the object code to use correct memory addresses.

### 5. What is compiler optimization?

Compiler optimization refers to techniques that compilers use to improve the performance and efficiency of the generated machine code. The goal of optimization is to make the compiled program run faster, consume less memory, or use fewer resources while maintaining the same behavior. These optimizations are applied during the compilation process and can be done at various levels (e.g., during code generation, instruction scheduling, and register allocation).

Types of Compiler Optimizations:

- Loop Optimization:

  - Loop Unrolling: This involves expanding loops to reduce the overhead of loop control. By unrolling loops, the compiler minimizes the number of iterations, which can increase execution speed by reducing jumps and improving instruction-level parallelism.
  - Loop Invariant Code Motion: Moves computations that do not change inside loops out of the loop to minimize redundant calculations.

- Constant Folding and Propagation:

  - Constant Folding: The compiler evaluates constant expressions at compile-time rather than runtime. For example, 3 * 4 is computed at compile time instead of each time the program is run.
  - Constant Propagation: When a variable is assigned a constant value, the compiler replaces all instances of that variable with the constant.

- Dead Code Elimination:

  - The compiler removes code that does not affect the program's output. For example, if a variable is assigned a value but never used, the compiler will eliminate the assignment.

- Inline Expansion:

  - The compiler replaces a function call with the actual code of the function. This avoids the overhead of function calls (e.g., saving registers, jumping to the function, etc.) and can improve performance, especially for small functions.
  - However, excessive inlining can increase the size of the executable, so compilers must use this optimization judiciously.

- Register Allocation:

  - The compiler assigns variables to machine registers to improve access speed. Using registers instead of memory can significantly reduce the time needed for data retrieval.

Levels of Optimization

- Level O (No Optimization):
  - This is default level where no optimizations are applied. This produces faster complation but results is less optimized code.
- Level 1 (Basic Optimization):
  - The compiler performs simple optimizations like constant folding, inlining, and dead code elimination.
- Level 2 (More Aggressive Optimization):
  - The compiler applies more advanced optimizations such as loop unrolling, stronger inlining, and instruction scheduling.
- Level 3 (Maximized Optimization):
  - The compiler applies the most aggressive optimizations available, including those that might significantly increase the size of the code. This level aims for the best performance at the cost of longer compile times.
- Profile-Guided Optimization (PGO):
  - The compiler collects runtime data and uses it to optimize the code based on how it is executed in real-world scenarios.

### 8. How to protect a header from being included again?

A traditional way to protect a header file from multiple inclusions is by using preprocessor directives:

```cpp
#ifndef HEADER_NAME_H  // Check if HEADER_NAME_H is not defined
#define HEADER_NAME_H  // Define HEADER_NAME_H

// Header file content here

#endif  // End of the conditional inclusion
```

Pros:
  
- Works in all C++ compilers
- Prevents multiple inclusions of the same file

Cons:

- Does not prevent cyclic dependencies (when two headers include each other)

How to Avoid Cyclic Dependencies

Cyclic dependencies happen when two or more headers include each other, causing an infinite inclusio loop.

- Forward Declarations
  - Instead of including a full header, declare the class in the header and include the full header in the `.cpp` file.
- Use `#include` Only When Necessary
  - Include a header only in the `.cpp` file if the header is not required in the `.h` file.

### 9. What are compilation flags?

Compilation flags are options passed to the compiler to control how a program is compiled and optimized. These flags can enable debugging, optimizations, warnings, and other behaviours.

Common Compilation Flags:

- Optimization Flags
- Debugging Flags
- Warning and Error Flags
- Standard Version Flags
- Predprocessor Flags
- Linking and Library Flags
- Output File Flags

### 11. What does the include directive do?

The `#include` directive tells the preprocessor to include the contents of another file into the current file before compilation. This is typically used to include header files (`.h` or `.hpp`) that contain function declarations, class definitions, macros, or constants.

How it Works:

- The preprocessor replaces the #include directive with the full content of the specified file before the actual compilation starts.
- This allows different files to share common definitions without rewriting code.

### 12. How do macros work?

A macro is a predprocessor directive that defines a name for a constant value, function-like expression, or block of code. When a macro is used, the preprocessor replaces all occurrences of the macro with its defined value before compilation begins (at the preprocessing stage).

How Macros Work:

- Macros are processed at he preprocessing stage (before compilation).
- They replace occurrences of the macro name with actual value or expression.
- They do not perform type checking, unlike functions.

## C Language

### 1. How does static affect global/local variables?

`Static` with Global Variables: a global variable declared with `static` limits its scope to the file where it is declared. A global `static` variable is allocated in the data segment at compile-time and is initialized before `main()` starts, during program startup phase.

- Without `static`: A global variable is externally visible and can be accessed from other files using `extern`.
- With `static`: The global variable is restricted to the current file, making it private to that file (also known as internal linkage).

`Static` with Local Variables: a local variable declared with static retains its value across function calls

- Without `static`: The variable is created and destroyed every time the function is called.
- With `static`: The variable persists throughout the program's execution but remains local to the function.

### 2. How does const affect a variable?

The `const` keyword in C++ makes a variable **read-only**, meaning its value cannot be modified after initialization.

### 3. What are the uses of extern?

The `extern` keyword is use to declare variables or functions that are defined in another translation unit (source file). It helps in linking global variables and function across multiple files.

-Common Uses of `extern`:

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

- Declaring a Function from Another File:
  If a function is defined in one file, we can use extern to access it in another file:

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

- Using `extern` with `const` Variables:
  By default, `const` variables have internal linkage (they are not visible outside the file). To use a `const` variable across files, we must declare it with `extern`:

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

  Without `extern`, `MAX_VALUE` would have file scope and could not be accessed in `file1.cpp`.

- Using `extern "C"` for C++ and C Compatibility:
  When working with C and C++ together, `extern "C"` is used to prevent C++ name mangling, allowing C++ to call C functions.

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

- Stack - stores local variables and function call information. Memory is allocated and deallocated automatically (LIFO structure).
- Heap - stores dynamically allocated variables (`new` in C++). Memory must be managed manually (`delete`).
- Data Segment (Static/Global Memory) - Stores global and `static` variables, divided into:
  - Initialized Data Segment - Stores global/static variables an initial value.
  - Uninitialized (BSS) Segment - Stores global/static variables without an initial value.
- Code Segment (Text Segment) - Stores executable program instructions.

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

### 18. What is a union?

A union in C and C++ is a special data structure that allows multiple members to share the same memory location. It enables storing different data types in the same memory space, but only one member of the union can hold a value at any given time. A union helps save memory by allowing different variables to use the same space, but at the cost of not being able to store values in multiple members simultaneously.

Key Features of a Union:

- Memory Sharing:
  - All members of a union share the same memory location. The size of a union is determined by the size of its largest member because the union must be large enough to store the largest data type.
- One Active Member
  - Only one member of the union can hold a value at any given time. When a new value is assigned to one member, it overwrites the value of the other members.
- Memory Efficiency
  - Unions help conserve memory when you need to store different types of data but do not need to use them simultaneously.

## C++/OOP

### 1. What is a class?

A class is a user-defined data type in C++ that encapsulates data members (variables) and member functions (methods) into a single unit. It provides absraction and encapsulation, allowing for modular and structured programming.

By default, all members of a class are `private`, meaning they are inaccessible from outside the class unless explicity specified as `public` or `protected`.

### 2. What is encapsulation? How is it implemented in C++? What is the difference between private/protected/public and where are they used?

Encapsulation is one of the fundamental principles of OOP. It refers to bundling data (variables) and methods (functions) that operate on the data into a single unit (class) and restricing direct access to some of the object's details. This helps in hiding implementation details and protecting data from unintended modification.

Encapsulation in C++ is implemented using access specifiers:

- `private` - members are only accessible within the same class.
- `protected` - members are accessible within the same class and derived (child) classes.
- `public` - members are accessible from outside the class.

### 3. What are the built-in types in C++?

Built-in types in C++ are fundamental data types provided by the language to represent various kinds of values such as integers, floating-point numbers, characters, and Boolean values.

### 4. What is an enum?

An enum (short for enumeration) is a user-defined type in C++ that represents a set of named integral constants. It helps make code more readable and maintainable by using meaningful names instead of raw numeric values.

- Unscoped Enum (C++98/C++03):
  - Defined using `enum` keyword
  - The underlying type is usually `int`.
  - Enum values are accessible without a scope.
  - Implicit conversion to integers is allowed.

  ```cpp
  #include <iostream>
  using namespace std;

  enum Color { RED, GREEN, BLUE };  // RED = 0, GREEN = 1, BLUE = 2

  int main() {
      Color c = GREEN;
      cout << "Color value: " << c << endl;  // Outputs: 1
      return 0;
  }
  ```

- Scoped Enum (C++11 and later)
  - Defining using `enum class`
  - Strongly typed (no implicit conversion to `int`)
  - Requires scope resolution (`EnumName::Value`)
  - More type-safe than unscoped enums.

  ```cpp
  enum class TrafficLight { RED, YELLOW, GREEN };

  int main() {
      TrafficLight t = TrafficLight::GREEN;
      // cout << t;  Error: No implicit conversion to int
  }

  ```

  Key Points:

  - Enums improve readability and code maintainability
  - Scoped enums prevent accidental conversions to integers
  - You can specify an underlying type using `:type` (e.g., `enum class Color : uint8_t`).

### 5. What is the relationship between a class and an object?

A class is a blueprint or template for creating objects. It defines the data members (variables) and member functions (methods) that describes the behavior of objects.

An object is an instance of a class, meaning it is a real-word entity that holds actual values based on the class definition.

### 6. What is the difference between a struct and a class?

- The main difference is default access specifiers
  - In a struct, members are public by default.
  - In a class, members are private by default.
- The default inheritance mode also differs:
  - A struct inherits publicly (public inheritance by default).
  - A class inherits privately (private inheritance by default).

### 7. What are the standard class methods for a class?

- Default Constructor
- Copy Constructor
- Move Constructor
- Copy Assignment Operator
- Move Assignment Operator
- Destructor

### 8. What is an abstract class and what is it for?

An abstract class is a class that cannot be instantiated directly. It serves as blueprint for other classes to derive from. An abstract class typically contains pure virtual functions (or virtual functions with no implementation) that must be implemented by its derived classes.

Puerpose of an Abstract Class:

- Define a common interface: It provides a common interface for all derived classes. Derived classes are required to implement the pure virtual functions.
- Polymorphism: It allows you to work with different derived objects through a pointer or reference to the base class, enabling polymorphism. This is often used in desingning systens like frameworks, UI components, or plugin architerctures.
- Prevent instantiations: Since an abstract class cannot be instantiated directly, it ensures that only derived classes with concrete implementations can be used.

### 9. How much memory does an object of an empty class A{}; take up?

It takes 1 byte.

### 10. What happens to a function if you add the static keyword to it? In the context of a class member? In the context of a class method?

When you add the `static` keyword to a member function in a class, it means that the function is not tied to a specific instance of the class. Instead, it is shared among all instances of the class. This function can be called without creating an object of the class.

- Static member characteristics:
  - It does not have access to the instance variables (non-static members) of the class, as it is not associated with a specific object.
  - It can only access other static members (both data and functions) of the class.
  - It can be called using the class name, like `ClassName::functionName()` or `ClassName::variableName`

### 11. What are the features of static class fields?

- A static member variable is shared by all instances of the class. There is only one copy of the static field, regardless of how many objects are created from the class. Every object will access the same memory location for that variable.
- A static field is initialized once when the program starts or when the class is first used, and it retains its value for the duration of the program.
- It is not tied to any particular object. Even if no instances of the class are created, the static field still exists.
- Static member variables can be accessed either via an instance of the class (though this is less common) or more commonly via the class name itself, e.g., ClassName::staticVariable.
- Static variables are useful when you need to store information that is shared by all instances of the class. For example, a static variable could be used for counting the number of instances created for that class, or for storing a constant value that should remain the same for every object.
- Static members can only access other static members of the class. They cannot access non-static members, because non-static members belong to a specific instance of the class.

### 12. What is the feature of constant class member methods?

- Const Member Function: Declared with const at the end of the function, ensuring no modification of the object's state.
- Const Objects: A const member function can be called on a const object, but it cannot modify any members of the object.
- Read-Only Access: const member functions are often used for methods that only read or return values, ensuring no side effects occur.

### 13. How to change a class field in a constant class method?

In C++, you cannot directly modify non-static class fields within a const member function because const methods guarantee that the object state will not change. However, there is a specific way to modify class fields inside a const method: using the mutable keyword.

The mutable keyword allows you to specify that a particular member variable of the class can be modified even in a const member function. This is useful for scenarios where you want to allow internal state changes (like caching or counters) without modifying the external state of the object.

### 14. What methods can be called from constant objects?

- A constant object can only call const member functions. These functions are guaranteed not to modify the state of the object. If you try to call a non-const method, the compiler will give an error because it might modify the object, which would violate the const contract.

- Static member functions can be called on a constant object because they do not operate on the instance of the object, but rather on the class itself. Static methods do not require a specific object to be called and do not modify the object's state, so they are allowed.

### 15. What is a heap and a stack? Difference, operating principle

Heap and Stack are two different regions of memory used for storig data during the execution of a program. They have different characteristics, operating principles, and use cases.

Heap is a region of memory used for dynamic memory allocation. When you allocate memory using `new` or `malloc`, the memory is allocated from the heap. Memory from the heap is allocated during runtime, and the programmer is responsible for managing the memory. If memory is no longer needed, the programmer must be explicitly release it using `delete` or `free`.

Stack is a region of memory used for storing local variables, function parameters, and return addresses. It operates in a last-in, first-out (LIFO) manner. Memory is automatically allocated and deallocated when a function is called or returns. When a function is called, its local variables are pushed onto the stack. When the function returns, the memory is automatically popped off the stack.

### 16. What is the difference between a pointer and a reference?

- Defination
  - Pointer: a variable that holds the address of another variable.
  - Reference: an alias for an exisiting variable.
- Nullability:
  - Pointer: can be `nullptr`
  - Reference: cannot be `null`: must refer to a valid object.
- Reassignability:
  - Pointer: can be reassigned to point to different addresses.
  - Reference: cannot be changed to refer to a different variable.
- Memory:
  - Pointer: Takes memory to store the addres
  - Reference: Takes no extra memory (just an alias).

### 17. What is a function pointer for? How to declare it?

### 18. What happens if you forgot to call delete? When will this memory be freed?

### 19. What is a smart pointer? What smart pointers are there in the standard library?

### 20. How does std::unique_ptr work?

### 21. How does std::shared_ptr work?

### 22. How does std::weak_ptr work?

### 23. Explain the constancy of a variable, reference, pointer. What is a constant pointer and a pointer to a constant? The size of a pointer in memory?

### 24. Explain the passing of arguments by value, by reference, and by pointer

### 25. Explain the order of evalution of function arguments?

### 26. WHat happens if you return a reference to a temporary object?

### 27. What is function overloading? Types of overloading

### 28. What is explicit and implicit type casting in C++? Explain the explicit type casting functions in C++

### 29. What is variable initialization in if statement?

### 30. What is lazy evaluatin C++?

Lazy evaluation in C++ is a technique where an expression or computation is delayed until its result is actually needed, rather than being computed immediately. This can improve performance by avoiding unnecessary calculations.

Examples of Lazy Evalution in C++:

- Short-Circuit Evalution in Logical Operators (`&&` and `||`):
  - The second operand is only evaluated if necessary:

  ```cpp
  bool func() {
    std::cout << "Function evaluated\n";
    return true;
  }

  int main() {
      bool result = false && func(); // `func()` is NOT called because `false && anything` is always false
      return 0;
  }
  ```

- Lazy Evaluation in Ranges (C++20):
  - The `views::transform` in the ranges library applies a transformation only when elements are accessed.

  ```cpp
  #include <iostream>
  #include <ranges>
  #include <vector>

  int main() {
      std::vector<int> nums = {1, 2, 3, 4, 5};

      auto lazyDoubled = nums | std::views::transform([](int x) {
          std::cout << "Doubling " << x << std::endl;
          return x * 2;
      });

      for (int num : lazyDoubled) {
          std::cout << num << " ";
      }

      return 0;
  }
  ```

- Lazy Initialization (Singleton Pattern):
  - The object is only created when it is first needed:

  ```cpp
  class Singleton {
  public:
      static Singleton& getInstance() {
          static Singleton instance;  // Created only when first called
          return instance;
      }
  private:
      Singleton() {}  // Private constructor
  };
  ```

### 31. What does the auto keyword do? auto definition of return type, function arguments?

The `auto` keyword automatically deduces the type of a variable or function return type at compile time. It helps reduce redundancy and improves readability.

- `auto` for Variable Type Deduction
  - Instead of explicitly defining a variable's type, `auto` allows the compiler to infer it:

  ```cpp
  #include <iostream>

  int main() {
      auto x = 10;        // int
      auto y = 3.14;      // double
      auto str = "Hello"; // const char*

      std::cout << x << " " << y << " " << str << std::endl;

      return 0;
  }
  ```

- `auto` in Function Return Type (C++ 11 and later)
  - The `auto` keyword can be used for return type deduction in functions:

  ```cpp
  auto add(int a, int b) {
    return a + b;  // Compiler deduces return type as int
  }

  int main() {
      std::cout << add(5, 3) << std::endl; // Output: 8
      return 0;
  }
  ```

- `auto` with `decltype` for Explicit Return Types
  - If the return type depends on complex expressions, use `decltype`:

  ```cpp
  #include <iostream>

  template <typename T1, typename T2>
  auto multiply(T1 a, T2 b) -> decltype(a * b) {
      return a * b; // Ensures correct return type
  }

  int main() {
      std::cout << multiply(3, 4.5) << std::endl; // Output: 13.5
      return 0;
  }
  ```

- `auto` in Function Arguments
  - `auto` cannot be used for function paremeters directly (expect in lambdas).

  ```cpp
  void func(auto x, auto y) { // ERROR: auto not allowed here
    std::cout << x + y;
  }
  ```

  - Correct way (Use Templates instead):

  ```cpp
  template <typename T, typename U>
  void func(T x, U y) {
      std::cout << x + y;
  }
  ```

  - However, `auto` works in lambda expressions:

  ```cpp
  auto lambda = [](auto x, auto y) { return x + y; };
  std::cout << lambda(3, 4.5);  // Output: 7.5
  ```

### 33. What is the difference between delete and delete[]? What happens if you can delete on an object created via new[]?

- `delete` vs `delete[]`
  - `delete` is used to free memeory allocated for a signle object using `new`.
  - `delete[]` is used to free memory allocated for an array of objects using `new[]`
- What happens if you use `delete` instead of `delete[]`?
  - If you use delete on array allocated with `new[]`, only the first element will be properly deleted, while the rest of the array may lead to memory leaks or undefined behaviour.
  - If you use `delete[]` on a single object allocated with new, the behavior is undefined. It may cause crashes, memory corruption, or unexpected behavior depending on the compiler and system.

### 34. Error handling in C++. What constructs are used when handling expections?

In C++, expeption handling is done using the `try-cathc` construct along with the `throw` keyword.

Basic Syntax

```cpp
try {
    // Code that might throw an exception
    throw std::runtime_error("An error occurred");
} 
catch (const std::exception& e) {
    std::cout << "Exception caught: " << e.what() << std::endl;
}
```

Example: Handling Different Types of Exceptions

```cpp
#include <iostream>
#include <stdexcept>

void testFunction(int value) {
    if (value < 0) 
        throw std::invalid_argument("Negative value is not allowed");
    if (value == 0)
        throw "Value cannot be zero"; // Throwing a string
}

int main() {
    try {
        testFunction(0);
    }
    catch (const std::invalid_argument& e) {
        std::cout << "Caught std::invalid_argument: " << e.what() << std::endl;
    }
    catch (const char* msg) {
        std::cout << "Caught exception: " << msg << std::endl;
    }
    catch (...) { 
        std::cout << "Caught an unknown exception" << std::endl;
    }
    return 0;
}
```

Exception Handling Best Practices

- Use `std::exception` hierarchy for standard expections (`std::runtime_error`, `std::logic_error`, etc)
- Catch expections by reference (`const std::exception &e`) to avoid slicing.
- Avoid throwing raw pointer or primitive types (`throw "error"`) use `std::runtime_error("error")` instead.
- Use `noexcept` for functions that don't throw exceptions to optimze performance.

### 35. Is it possible to throw an exception from a constructor? What fields will be constructed, what fields will be destroyed?

Yes, it is possible to throw an exception from a constructor. However, if an exception is throwm before the object is fully constructed, the object will not be created, and destructors will not be called for that object.

### 36. What is a memory leak?

A memory leak occurs when dynamically allocated memory (using `new`, `malloc`, etc.) is not properly deallocated (`delete`, `free`). As a result, the memory remains occupied but inaccessible, leading to increased memory usage and potential crashes.

### 37. Is it possible to throw an exception from a destructor?

Yes, it is possible to throw an exception from a destructor, but it is highly discouraged because it can lead to program termination due to double exception.

If necessary, catch and handle them inside the destructor.

### 38. What is a lambda function in C++? How to access variables in the outer scope?

A lambda function in C++ is an anonymous function (i.e., without name) that can be defined inline inside another function. It is often used for short, one-time operations, especially in STL algorithms or multithreading.

Syntax of a Lambda Function

```cpp
[ capture_list ] ( parameters ) -> return_type {
    function_body
};
```

- `capture_list` - specifies which outer-scope variables are captured.
- `parameters` - arguments like in a normal function
- `return_type` (optional) - specifies the return type
- `function_body` - contains the function logic.

```cpp
#include <iostream>
using namespace std;

int main() {
    auto add = [](int a, int b) {
        return a + b;
    };

    cout << "Sum: " << add(5, 10) << endl;  // Output: Sum: 15
}
```

Capturing Outer Scope Variables

Lambda functions can access variables from the surrounding scope using capture lists.

Capture by Value (`[=]` or `[var]`)

The lambda gets a copy of the variable (modifications inside lambda won't affect the original variable)

```cpp
int x = 10;
auto lambda = [x]() { cout << x << endl; };  // x is captured by value
lambda();
```

Capture by Reference (`[&]` or `[&var]`)

The lambda modifies the original variable

```cpp
int x = 10;
auto lambda = [&x]() { x++; };  // Capture by reference
lambda();
cout << x;  // Output: 11 (x is modified)
```

Capture Everything (`[=]` or `[&]`)

- `[=]` - Captures all outer variables by value
- `[&]` - Captures all outer variables by reference

```cpp
int a = 5, b = 10;

auto lambda1 = [=]() { cout << a + b << endl; };  // Captures both a and b by value
auto lambda2 = [&]() { b *= 2; };  // Captures both a and b by reference

lambda1();  // Output: 15
lambda2();  
cout << b;  // Output: 20 (b is modified)
```

Using `mutable` in a Lambda

By default, lambdas capture by value as `const`, so modifying variables inside is not allowed. Use `mutable` to allow modifications inside the lambda.

```cpp
int x = 10;
auto lambda = [x]() mutable { x++; cout << x; };  // Modifies captured copy of x
lambda();  // Output: 11
cout << x;  // Output: 10 (original x is unchanged)
```

Returning a Value Explicitly

```cpp
auto square = [](int x) -> int {
    return x * x;
};

cout << square(4);  // Output: 16
```

### 41. What is namespace, anonymous namespace used for?

A namespace in C++ is used to group related code elements (like variables, function and classes) under a unique name to avoid name conflicts in large projects.

Why Use a Namespace?

- Prevent name conflicts in large codebases.
- Organizes code logically
- Enables better code modularity.

An anonymous namespace is a namespace without a name. It makes all the declarations inside it local to the translation unit (i.e., the current .cpp file).

Why Use an Anonymous Namespace?

- Hides functions/variables from other files
- Prevents name conflicts in different files
- Works as an alternative to `static` for file-local scope.

### 42. How to call an object from nested namespace?

When working with nested namespaces, you need to use the fully qualified name (i.e., include all levels of the namespace) to access objects inside them.

### 43. How do inline function work? Can such a function be recursive?

An inline function in C++ is a function that suggests the compiler to replace its function call with the actual function body at compile time. This reduces function call overhead and can improve performance, especially for small functions.

Technically, a recursive function can be marked as inline, but it will not actually be inlined by the compiler because recursion requires multiple function calls.

### 44. What is polymorphism?

Polymorphism in C++ allows a function or method to have different behaviours depending on the object that is calling it. This enables dynamic method resolution at runtime.

Types of Polymorphism in C++

- Compile-Time (Static) Polymorphism
  - Achieved through function overloading and operator overloading
  - Resolved at compile time
- Run-Time (Dynamic) Polymorphism
  - Achieved using virtual functions and inheritance
  - Resolved at runtime using vtabel (virtual table)

### 45. What is inheritance used for?

Inheritance in C++ allows a child (derived) class to acquire the properties and behaviors of a parent (base) class. It is a fundamental concept of Object-Oriented Programming (OOP) used for code reusability, extensibility, and hierarchy modeling.

### 46. What are types of inheritance?

C++ supports single and multiple types of inheritance to define relationships between classes.

### 47. How can you solve the diamond inheritance problem without using virtual inheritance?

- Manually Disambiguate Calls (Using Scope Resolution Operator `::`)
- Use Composition

### 48. What happens if you pass a child class by value to function that takes a base class?

When you pass a child class object by value to a function that takes a base class parameter, object slicing occurs. This means that only the base class portion of the child object is copied, and any derived class-specific data or overridden methods are lost.

### 50. What happens if you call overridden virtual function from constructor? Can a constructor be virtual?

No, constructor cannot be virtual. The reson is that constructors are responsible for creating an object, and virtual dispatch requires an already constructed object.

If a base class constructor calls a virtual function, it does not call the overridden version in the derived class. Instead, it calls the base class's own version of the function.
Reason: During the base class constructor execution, the derived class has not been fully constructod yet, so its version of the function is not available.

### 51. Can a pure virtual function have an implementation? What happens if you call a pure virtual function from a constructor?

- A pure virtual function must be overridden in derived classes and makes the base class abstract, preventing direct instantiation.
- Calling a pure virtual function inside a constructor can lead to underfined behaviour unless the base class provides an implementation
- Constructors do not call overridden functions in derived classes because the derived class in not yet initialized.

### 52. What methods are generated for a class by default? In what case will such methods not be generated? How can I force the compiler to add/remove these methods?

### 53. How can I prevent a class from being inherited?

To prevent a class from being inherited in C++, you can use the `final` specifier. When applied to a class, it ensures that the class cannot be used as a base class for futher inheritance.

### 54. What is the order of class construction and destruction in the hierarchu? The order of class field initialization?

Base class constructor first: When an object of a derived class is created, the constructor of the base class is called first, followed by the constructors of any intermediate classes (if any), and then the constructor of the derived class.

This ensures that the base class is properly initialized before the derived class starts initializing its members.

Derived class destructor last: During object destruction, the derived class destructor is called first, followed by destructors of intermediate classes (if any), and finally the destructor of the base class.

This order ensures that the derived class resources are cleaned up first before the base class resources.

### 55. What are the ways to initialize class fields?

- Initialization List: Fields can be initialized directly in the constructor's initialization list, which is generally the preferred way, especially for constant members, references, or when performance is a concern.
- Inside Constructor Body: Fields can also be initialized inside the constructor's body. However, this approach is not as efficient as the initialization list because the fields are first default-initialized and then assigned new values.
- Default member initializations (Since C++11)
- Static member initializations

### 56. Can a destructor be virtual?

A destructor can be virtual in C++. In fact, it is highly recommended to make the destructor virtual in a base class when dealing with inheritance, especially if objects of derived classes might be deleted through pointers to base class objects. This ensures that the destructor of the derived class is called when an object is deleted, avoiding potential memory leaks or undefined behavior.

When you use inheritance, if a base class pointer is used to delete an object of a derived class, the base class destructor will be called by default. This can lead to problems if the derived class has additional resources (e.g., dynamically allocated memory) that need to be cleaned up properly. A virtual destructor ensures that the appropriate destructor for the derived class is called, allowing proper cleanup of resources.

### 57. What does the virtual keyword do?

The virtual keyword in C++ is used to declare functions that can be overridden in derived classes, enabling polymorphism. When a function is marked as virtual, the C++ compiler ensures that the correct function (derived class version) is called, even if the function is called through a pointer or reference to the base class.

### 58. How to protect an object from being copied?

To prevent an object from being copied, you can delete or make the copy constructor and the copy assignment operator inaccessible. In C++11 and later, this can be achieved using the delete keyword.

### 59. What is move semantics?

Move semantics is a feature introduced in C++11 that allows resources (such as memory, file handles, etc) to be transferred from one object to another efficiently without copying the data. It enables moving rather than copying when temporary (r-value) are involved.

In traditional copy semantics, when an object is copied, its data members are duplicated, which can be inefficient (especially for large objects). Move semantics avoid this overhead by transferring ownership of the resources from one object to another instead of copying them.
