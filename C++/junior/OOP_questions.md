# Juniour

## C++/OOP

### 1. What is a class?

A class is a user-defined data type in C++ that encapsulates data members (variables) and member functions (methods) into a single unit. It provides abstraction and encapsulation, allowing for modular and structured programming.

By default, all members of a class are `private`, meaning they are inaccessible from outside the class unsless explicitly specified as `public` or `protected`.

### 2. What is encapsulation? How is it implemented in C++? What is the difference between private/protected/public and where are they used?

Encapsulation is one of the fundamental principles of OOP. It refers to bundling data (variables) and methods (functions) that operate on the data into a single unit (class) and restricing direct access to some of the object's details. This helps in hiding implementation details and protecting data from unintended modification.

Encapsulation in C++ is implemented using access specifiers:

- `private` - members are only accessible within the same class.
- `protected` - members are accessible within the same class and derived (child) classes.
- `public` - members are accessible from outside the class.

### 3. What are the built-in types in C++?

Built-in types in C++ are fundamental data types provided by the language to represent various kinds of values such as integers, floating-point numbers, characters, and boolean values.

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

Purpose of an Abstract class:

- Define a common interface: It provide a common interface for all derived classes. Derived classes are required to implement the pure virtual functions.
- Polymorphism: It allows you to work with different derived objects through a pointer or reference to the base class, enabling polymorphism. This is often used in desingning systems like frameworks, UI components, or plugin architectures.
- Prevent Instantiations: Since an abstract class cannot be instatntiated directly, it ensures that only derived classes with concrete implementations can be used.

### 9. How much memory does an object of an empty class A{}; take up?

It takes 1 byte.

### 10. How much memory does an object of an empty enum take up?

By default, in C++, an enum has an underlying type of int, which usually takes 4 bytes on most systems. Even if the enum doesn't have any enumerators, the compiler still needs to give it a size for type safety and memory layout.

### 11. What happens to a function if you add the static keyword to it? In the context of a class member? In the context of a class method?

When you add the `static` keyword to a member function in a class, it means that the function is not tied to a specific instance of the class. Instead, it is shared among all instances of the class. This function can be called without creating an object of the class.

- Static member characteristics:
  - It does not have access to the instance variables (non-static members) of the class, as it is not associated with a specific object.
  - It can only access other static members (both data and functions) of the class.
  - It can be called using the class name, like `ClassName::functionName()` or `ClassName::variableName`

### 12. What are the features of static class fields?

- A static member variable is shared by all instances of the class. There is only one copy of the static field, regardless of how many objects are created from the class. Every object will access the same memory location for that variable.
- A static field is initialized once when the program starts or when the class is first used, and it retains its value for the duration of the program.
- It is not tied to any particular object. Even if no instances of the class are created, the static field still exists.
- Static member variables can be accessed either via an instance of the class (though this is less common) or more commonly via the class name itself, e.g., ClassName::staticVariable.
- Static variables are useful when you need to store information that is shared by all instances of the class. For example, a static variable could be used for counting the number of instances created for that class, or for storing a constant value that should remain the same for every object.
- Static members can only access other static members of the class. They cannot access non-static members, because non-static members belong to a specific instance of the class.

### 13. What is the feature of constant class member methods?

- Const Member Function: Declared with const at the end of the function, ensuring no modification of the object's state.
- Const Objects: A const member function can be called on a const object, but it cannot modify any members of the object.
- Read-Only Access: const member functions are often used for methods that only read or return values, ensuring no side effects occur.

### 14. How to change a class field in a constant class method?

In C++, you cannot directly modify non-static class fields within a const member function because const methods guarantee that the object state will not change. However, there is a specific way to modify class fields inside a const method: using the `mutable` keyword.

The `mutable` keyword allows you to specify that a particular member variable of the class can be modified even in a const member function. This is useful for scenarios where you want to allow internal state changes (like caching or counters) without modifying the external state of the object.

### 15. What methods can be called from constant objects?

- Constant objects: can only call const member functions. These functions are guaranteed not to modify the state of the object. If you try to call a non-const method, the compiler will give an compilation error because it might modify the object, which would violate the const contract.
- Static Members functions: can be called on a constant object because they do not operate on the instance of the object, but rather on the class itself. Static methods do not require a specific object to be called and do not modify the object's state, so they are allowed.

### 16. What is a heap and a stack? Difference, operating principle

Heap and Stack are two different regions of memory used for storing data during the execution of a program. They have different characteristics, operating principles, and use cases.

Heap is a region of memory used for dynamic memory allocation. When you allocate memory using `new` or `malloc`, the memory is allocated from the heap. Memory from the heap is allocated during runtime, and the programmer is responsible for managing the memory. If memory is no longer needed, the programmer must be explicitly release it using `delete` or `free`.

Stack is a region of memory used for storing local variables, function parameters, and return addresses. It operates in a last-in, first-out (LIFO) manner. Memory is automatically allocated and deallocated when a function is called or returns. When a function is called, its local variables are pushed onto the stack. When the function returns, the memory is automatically popped off the stack.

### 17. What is the difference between a pointer and a reference?

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

### 18. What is a function pointer for? How to declare it?

Function pointer is a pointer that point to function. It allows us to store the address of a function and call it indirectly. Functions pointer are useful for:

- Callback Functions: Passing a function as an argument to another function.
- Event Handling: Handling different types of events dynamically by associating specific actions with event handlers.
- Dynamic function selection: Choosing between different functions to execute at runtime.

```cpp
return_type (*pointer_name)(parameter_types);
```

### 19. What happens if you forgot to call delete? When will this memory be freed?

You will face with a **memory leak**. This means that the memory allocated dynamically (usually using `new` or `new[]`) will not be deallocated and thus remains occupied for the duration of the program. Over time, if this happens repeatedly or on a large scale, memory leaks can lead to increased memory usage, and eventually, your program might run out of memory, causing it to crash or slow down.

How to prevent memory leaks:

- Always call `delete` or `delete[]` after using `new` or `new[]` to free dynamically allocated memory.
- `Use smart pointers`: In modern C++, you should use smart pointers (`std::unique_ptr`, `std::shared_ptr`) from the C++ Standard Library. These manage memory automatically and ensure that memory is freed when the smart pointer goes out of scope, reducing the chances of memory leaks.
- `Use RAII (Resource Acquisition Is Initialization)`: This C++ programming principle ensures that resources (like memory, file handles, or network connections) are acquired during object creation and released when the object goes out of scope. Smart pointers are a common example of RAII in action.
- Use tools:
  - `Valgrind`: A popular tool for detecting memory leaks and other memory-related issues in C++ programs.
  - `Static Analysis`: Use tools like `Clang` or `GCC`'s static analysis tools to identify potential memory management problems.
