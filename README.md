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


### 8. How to protect a header from being included again?

### 9. What are compilation flags?

### 10. How to protect a header from being included again?

### 11. What does the include directive do?

### 12. How do macros work?
