# Junior

## Metaprogramming questions

### 1. What is a template class and a template function?

Templates in C++ allow writing **generic code** that works with different data types. They help **reduce code duplication** by enabling functions and classes to handle multiple data types without rewriting the same logic.

**Template Function** is a function that works with any data type, determined at **compile-time**.

**Template Class** allows defining a class that operates on any data type.

**Advantages of Templates**:

- Reduces Code Duplication - no need to write separate versions for different types.
- Type-Safe - the compiler ensures type correctness at compile-time.
- More Generic and Reusable - the same logic can be use for multiple types.

**Disadvantages of Templates**:

- Code Bload: For every type used, a separate version of the function/class is generated, which can increase binary size.
- Complex Compilation Errors: Errors with templates can be hard to read and debug, especially for beginners.
- Longer Compile Times: Since the compiler needs to instantiate templates for every type used, compilation can slow down.
- Poor IDE Support (in some cases): Some IDEs or static analysis tools struggle with parsing and providing accurate info for heavily templated code.
- Lack of Separation Between Interface and Implementation: You usually need to define template functions in the header file, exposing implementation details.

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

- **Virtual functions rely on dynamic dispatch (VTable mechanism)** - they are resolved at runtime based on the actual type of the object.
- **Templates rely on compile-time instantiation** - template functions are generated during compilation for each specific type used.

Since virtual functions require a fixed function signature in the VTable, they cannot be templated, as templates generate different versions for different types at compile-time.

**What is the Alternative?**:

If you need template-like behaviour with polymorphism, you can use non-template virtual functions in combinations with templated base classes or **CRTP** (**Curriously Recurring Template Pattern**).

**What If You Need a Template-Like Virtual Function?**:

A workaround is the use CRTP:

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

- Explicit specialization (Custom implementation for a specific type)

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

Template specialization allows to define a custom implementation for a specific type or set of types when using a template. Instead of relying on the general template logic, you can provide a specialized version of the template that is used when the template is instantiated with a particular type.

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
template <typename T>
class MyClass {
public:
    void print() {
        std::cout << "Generic template" << std::endl;
    }
};

// Partial specialization for pointer types (T*)
template <typename T>
class MyClass<T*> {
public:
    void print() {
        std::cout << "Partially specialized template for pointer type" << std::endl;
    }
};

int main() {
    MyClass<double> obj1;      // Uses the general template
    MyClass<int*> obj2;        // Uses the specialized template for pointers

    obj1.print();  // Output: Generic template
    obj2.print();  // Output: Partially specialized template for pointer type

    return 0;
}
```

### 7. Tell us about implementing template classes in a cpp file?

Implementing template classes in a .cpp file requires a slightly different approach than implementing regular non-template classes because templates are instantiated at compile time and must be available to the compiler in the header file (or at least in the translation unit where they are used).

**Why Can't Template Class Definitions Be in a `cpp` File?**

Templates are **compile-time constructs**, meaning the actual code is generated when you instantiate a template with a specific type. The defition of the template must be visible to all translation units that use it, so you can't just define template classes in a `.cpp` file.

To manage this, template class definitions are usually included in `header files` (`.h` or `.hpp`). However, you can still define template member functions in a separate `.cpp` file using explicit instantiation.
