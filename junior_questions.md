# Juniour

## Genaral questions

### 1. What are the basic principles of OOP?

- `Encapsulation` - The bundling of data (variables) and methods (functions) that operate on the data into a single unit (class) while restricting direct access to some details. This is typically achieved using access specifiers like `private`, `protected`, and `public`. Encapsulation helps in data hiding and enforcing modular design.

- `Inheritance` - A mechanism where one class (child/derived class) inherits attributes and behaviours (methods) from another class (parent/base class). This promotes code reusability and establishes a relationship between classes (e.g., `class Dog : public Animal{}` means `Dog` inherits from `Animal`).

- `Polymorphism` - The ability of different classes to be treated as instances of the same class through a common interface. This allows methods with the same name to behave differently based on the object they operate on. It is achieved via:
  - `Compile-time (Static) Polymorphism` - Achieved using function overloading and operator overloading.
  - `Run-time (Dynamic) Polymorphism` - Achieved using method overriding with virtual functions and dynamic dispatch.

- `Abstraction` - Hiding implementation details and exposing only the necessary functionaly. THis is often achieved through abstract classes and interfaces (pure virtual functions in C++).

## 2. What is the algorithm complexity?

Algorithm complexity refers to the measurement of how an algorithm's resource consumption grows relative to the input size. It is primarily analyzed in terms of:

**Time Complexity** – Describes how the execution time of an algorithm increases as the input size grows. It is commonly expressed using `Big-O` notation, which represents the upper bound of the growth rate (e.g., `O(1)`, `O(log N)`, `O(N)`, `O(N²)`, etc.).

**Space Complexity** – Describes the amount of memory an algorithm requires as the input size grows. It includes both the auxiliary space used by the algorithm and the input storage itself.

`Big-O` notation provides an abstract way to describe the worst-case or upper-bound growth rate of an algorithm. Some common complexities are:

- `O(1)` – Constant Time: Execution time remains the same regardless of input size (e.g., accessing an array element by index).
- `O(log N)` – Logarithmic Time: Execution time grows logarithmically, often seen in divide-and-conquer algorithms (e.g., binary search).
- `O(N)` – Linear Time: Execution time grows proportionally with input size (e.g., iterating over an array).
- `O(N²)` – Quadratic Time: Execution time grows quadratically, often seen in nested loops (e.g., bubble sort).
`- O(2ⁿ)` – Exponential Time: Execution time doubles with each additional input size (e.g., recursive Fibonacci without memoization).

## 3. Explain such data structures as stack and queue

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

## 4. What interesting things have you found in the new standarts C++17, C++20?

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

## 5. What is the ASCII table?

The ASCII (American Standard Code for Information Interchange) table is a character encoding standard that assigns a unique numerical value to characters, including letters, digits, punctuation, and control characters.

- Size: ASCII uses 7 bits to represent characters, allowing 128 unique values (0-127). Homever, it is often stored in 1 byte (8 bits), with the extra bit sometimes used for error checking or extended character sets.
- Structure:
  - `0-31`: Control characters (e.g., `\n` (newline), `\t` (tab), `\0` (null)).
  - `32-126`: Printable characters (letters, numbers, symbols).
  - `127`: DEL (delete) character
- Extended ASCII: Some systems use 8-bit ASCII (0-255), which includes additional special and international characters.

## 6. What is Unicode?

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

## 7. What are unit tests for?

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

## 8. What is difference between unit and intergration tests?

- **Unit Tests** ensure that individual functions/classes work correctly in isolation.
- **Integration Tests** check if multiple components (e.g., database, API work together properly).

**Testing Freworks**: GoogleTest, Catch2, Boost.Test.

## 9. What is TDD?

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
