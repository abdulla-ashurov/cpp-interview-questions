# JUNIOR

## STL/Algorithms

### 1. What does STL consist of?

The STL consists of three main components:

- **Containers** are data structures that store collections of objects. They can be classified into three types:
  - Sequential Containers (store elements in a linear fashion):
    - `std::vector` (dynamic array)
    - `std::list` (double linked list)
    - `std::dequeu` (double-ended queue)
    - `std::array` (fixed-size array)
    - `std::forward_list` (single linked list)
  - Associative Containers (store elements in sorted order):
    - `std::set` (unique sorted elements)
    - `std::map` (key-value pairs with unique keys)
    - `std::multiset` (allows duplicate elements)
    - `std::multimap` (key-value pairs with duplicate keys)
  - Unordered Containers (store elements in hashed order for faster lookup)
    - `std::unordered_set`
    - `std::unordered_map`
    - `std::unordered_multiset`
    - `std::unordered_multimap`

- **Iterators** provide a way to traverse elements in a container. They act like pointers and allow access to container elements sequentially. There are different types of iterators:
  - **Input Iterator** - reads data (e.g., `std::istream_iterator`)
  - **Output Iterator** - writes data (e.g., `std::ostream_iterator`)
  - **Forward Iterator** - moves forward in one direction (e.g., `std::forward_list::iterator`)
  - **Biderectional Iterator** - moves both forward and backward (e.g., `std::list::iterator`)
  - **Random Access Iterator** - allows jumping to any position (e.g., `std::vector::iterator`)

- **Algorithms**: STL provides a set of built-in algorithms for performing operations on containers, such as:
  - **Sorting & Searching**: `std::sort`, `std::binary_search`, `std::find`
  - **Modifying**: `std::reverse`, `std::remove`, `std::replace`
  - **Numerical Operations**: `std::accumulate`, `std::iota`
  - **Set Operations**: `std::set_union`, `std::set_intersection`
  - **Heap Opeartions**: `std::make_heap`, `std::push_heap`, `std::pop_heap`.

Other Components (Additional but Important)

Besides the three main components, STL also includes:

- **Functors (Function Objects)** - customizable behaviour for algorithms
- **Allocators** - memory management (e.g., `std::allocator`)
- **Utility Components** - `std::pair`, `std::tuple`, `std::optional`.

### 2. What algorithms have you been used with STL? What is the advantage of using algorithms over hand-written functions?

- **Performance Optimization** - STL algorithms are optimzed for speed and memory efficiency.
- **Reliability & Maintainability** - they are well-tested and reduce the risk of errors
- **Code readability & Simplicity** - code becomes clearner and more expressive.
- **Generic & Reusable** - work with various containers (`std::vector`, `std::list`, `std::array`, etc)
- **Standardized & Portable** - consisted accross different compilers and platforms.

### 3. Tell us about the standard library containers vector, list, map, unordered_map

- `std::vector` (Dynamic Array - Sequential Container):
  - A dynamic array that automatically resizes when needed
  - Provides fast access `O(1)` to elements via indexing.
  - Operations:
    - `push-back()` - adds an element to the end (`O(1)` amortized).
    - `pop_back()` - removes the last element (`O(1)`)
    - `insert()` - inserts elements (`O(n)` in the worst case)
    - `erase()` - removes elements (`O(n)` in the worst case)
  - Use case: When frequent random access is required but insertions/deletions in the middle are rare.

- `std::list` (Double Linked List - Sequential Container)
  - A double linked list where elements are linked with pointers.
  - Support fast insertions & deletions (`O(1)`) anywhere in the list
  - Operations:
    - `push_back()/push_front()` - Insert elements at the end/beginning (`O(1)`)
    - `erase()` - removes an element (`O(1)`, given an iterator)
    - `size()` - returns the number of elements (`O(n)` in some implementations).
  - Use case: When frequent insertions/deletios in the middle are required, but random access is not needed.

- `std::map` (Ordered Associative Container - Balanced BST, `O(log n)`)
  - A sorted associative container implemented as a `Red-Black Tree`
  - Stores key-value pairs where keys are sorted.
  - Operations:
    - `insert({key, value})` - inserts a key-value pair (`O(log n)`).
    - `erase(key)` - removes an element by key (`O(log n)`)
    - `find(key)` - searches for a key (`O(log n)`)
  - Use case: When ordered keys are required and frequent searches/modification are needed.

- `std::unordered_map` (Unordered Associative Container - Hash Table `O(1)`)
  - Stores key-value pairs but does not maintain orde
  - Uses a hash table for average O(1) lookup, insertion, and deletion
  - Operations:
    - `insert({key, value})` - inserts a key-value pair (`O(1)` average, `O(n)` worst case).
    - `erase(key)` - removes an element by key (`O(1)` average, `O(n)` worst case)
    - `find(key)` - searches for a key (`O(1)` average, `O(n)` worst case)
  - Use case: When fast lookups are the priority and ordering is not required.

**Amortized O(1)** means that an operation usually takes constant time (O(1)), but occasionally, it may take longer (e.g., O(n)). However, when averaged over multiple operations, the time complexity remains O(1) per operation.

### 4. What types of iterators do you know? How are they different? What containers are they used in?

**Iterators** provide a way to traverse elements in a container. They act like pointers and allow access to container elements sequentially. There are different types of iterators:

- **Input Iterator** - reads data (e.g., `std::istream_iterator`)
- **Output Iterator** - writes data (e.g., `std::ostream_iterator`)
- **Forward Iterator** - moves forward in one direction (e.g., `std::forward_list::iterator`)
- **Biderectional Iterator** - moves both forward and backward (e.g., `std::list::iterator`)
- **Random Access Iterator** - allows jumping to any position (e.g., `std::vector::iterator`)

### 5. What is the difference between std::set, std::map, std::unordered_multimap?

- `std::set`:
  - Stores unique elements in sorted order
  - Implemented as a self-balancing BST (e.g., Red-Black Tree)
  - Operations like `insert()`, `find()`, and `erase()` take `O(log n)` time

- `std::map`:
  - Stores key-value pairs in sorted order (by key)
  - Implemented as a self-balancing BST (e.g., Red-Black Tree)
  - Keys must be unique, but values can be different
  - Operations like `insert()`, `find()`, and `erase()` take `O(log n)` time

- `std::unordered_multimap`
  - Stores key-value pairs in no particular order.
  - Impelented using hash table for fast lookup
  - Allows duplicate keys, meaning multiple values can exist for the same key
  - Operations like `insert()`, `find()`, and `erase()` take `O(1)` average case, but `O(n)` worst case (when hash collision occur)

### 6. What is the remove-erase idiom?

The **remove-erase idiom** is a common technique in C++ used to efficiently remove elements from standard library containers like `std::vector` and `std::deque`. It is necessary because `std::remove` alone does not actually remove elements from a container - it only moves the elements to be removed to the end and returns an iterator to the new logical end.

How it Works

```cpp
vec.erase(std::remove(vec.begin(), vec.end(), value), vec.end());
```

Explanation:

- `std::remove(vec.begin(), vec.end(), value)`
  - Moves all occurences of `value` to the end of the vector
  - Returns an iterator to the new logical end of the vector
- `vec.erase(..., vec.end())`
  - Actually removes the "moved" elements by erasing everything from the returned iterartor to `vec.end()`

### 7. How to get the smallest value of a type?

Using `<limits>` (Recommended)

```cpp
#include <iostream>
#include <limits>

int main() {
    std::cout << "Smallest int: " << std::numeric_limits<int>::min() << "\n";
    std::cout << "Smallest double: " << std::numeric_limits<double>::min() << "\n"; // Smallest positive double
    std::cout << "Smallest negative double: " << -std::numeric_limits<double>::max() << "\n";
}
```

Key Points:

- Use `<limits>` for a portable solution that works for all types
- Be careflu with floating points: `std::numeric_limits<double>::min()` returns the **smallest positive value**, not the most negative value.
  - To get the **most negative value**, use `-std::numeric_limits<double>::max()`

Note: `<limits>` follows IEEE 754 floating-point conventions.

### 8. What is the difference between std::map and std::unordered_map?

- Ordering:
  - `std::map`: keys are stored in sorted order (based on `<` operator)
  - `std::unordered_map`: keys are stored in no specific order

- Implementation:
  - `std::map`: implemented as a balanced binary tree (Red-Black Tree)
  - `std::unordered_map`: implemented as a hash table

- Time Complexity:
  - `std::map`: Lookup, insert, and erase: `O(log N)` (due to tree operations)
  - `std::unordered_map`: Average case: `O(1)`, Worst Case: `O(N)` (due the hash collision)

- Memoery Usage:
  - `std::map`: Uses more memory due to tree structure overhead
  - `std::unordered_map`: Generally uses more memory due to hash table buckets

- Key Lookup:
  - `std::map`: Efficent when keys are needed in sorted order
  - `std::unordered_map`: Efficent for fast lookups without order

- When to Use?
  - `std::map`: When you need ordered keys and range queries (e.g., `lower_bound`, `upper_bound`)
  - `std::unordered_map`: When you need fast lookups with no ordering (e.g., frequency counting, caching)

### 9. How to count the number of elements in std::list?

Use `std::list::size()`, if `size()` is not existed then use `std::dintance` to count of size.

### 10. What is the difference between vector and list and when is it better to use them?

Use `std::vetor` when:

- You need fast random access
- You mainly add/remove elements at the end
- Memory efficiency and cache locality matter
- You perform many sequential iterations

Use `std::list` when:

- You need frequent insertions/deletions in the middle
- You don't require random access
- Reallocation overhead of `vector` is a concern
- List-specific features like `splice()` are useful

## Multithreading

### 1. What do you know about multithreading?

Multithreading is a technique that allows a program to execute multiple tasks (threads) concurrently within a single proces. This can improve performance by utilizing multiple CPU cores.

Key Concepts in Multithreading:

- Threads (`std::thread`) - the basic unit of execution in multithreading.
- Synchronization Mechanisms - used to prevent race conditions and ensure safe access to shared resources:
  - `std::mutex`, `std::lock_guard`, `std::unique_lock`
  - `std::condition_variable`
- Atomic Operations - `std::atomic` provides lock-free operations for simple data types.
- Thread Communication - using condition variables, message queues, or thread-safe containers
- Thread Polling - managing a set of reusable threads (`std::async`, thread pools)
- Parallel Execution (`std::future`, `std::async`) - running tasks asynchronously without manually managing thread.

### 2. What are the simmilarities and differences between processes and thread?

- Definition:
  - Process: a running instance of a program
  - Thread: a smaller unit of execution within a process

- Memory:
  - Process: each process has its own memory space (isolated)
  - Thread: share the same memory space within a process.

- Communication:
  - Process: requires Inter-Process Communication (IPC) (pipes, shared memory, message queues)
  - Thread: can communicate easily via shared memory

- Creation Overhead:
  - Process: high (OS allocates new memory and resources)
  - Thread: low (just spawns a new thread within the same process)

- Context Switching:
  - Process: slow (requires switching memory address space)
  - Thread: fast (stays within the same memory space)

- Fault Isolation:
  - Process: a crash in one process does not affect others
  - Thread: a crash in one thread may crash the entiry process

- Parallelism:
  - Process: can run on different CPU cores independently
  - Thread: can run on multiple cores but shares resources.

Process Example (using `fork` in Linux):

```cpp
#include <iostream>
#include <unistd.h>  // For fork()

int main() {
    pid_t pid = fork();
    
    if (pid == 0) {
        std::cout << "Child process\n";
    } else {
        std::cout << "Parent process\n";
    }
    return 0;
}
```

Thread Example (using `std::thread`)

```cpp
#include <iostream>
#include <thread>

void work() {
    std::cout << "Thread is running\n";
}

int main() {
    std::thread t(work);
    t.join();  // Wait for thread to finish
    return 0;
}
```

### 3. How to synchronize information transfers between threads?

To synchronize information transfers between threads, you need to ensure that one thread does not interfere with another thread when accesing shared data. This is essential because multiple threads accessing and modifying shared data simultaneosly can lead to race conditions, where the final resul depends on the order of execution, potentially causing unexpected behaviour.

Here are the most common synchronization mechanism in C++:

- Mutexes (Mutual Exclusion): a mutex is synchronization primitive that can be locked and unlocked. It ensures that only one thread can access a shared resource at a time.

  - `std::mutex` is used to protect data from being accessed simultaneously by multiple threads
  - `std::lock_guard` is a helper that automatically locks and unlocks a mutex, providing better exception safety.

  ```cpp
  #include <iostream>
  #include <thread>
  #include <mutex>

  std::mutex mtx;  // Mutex to protect shared resource

  void print_shared_data(int i) {
      std::lock_guard<std::mutex> lock(mtx);  // Locks the mutex automatically
      std::cout << "Thread " << i << " is accessing shared data.\n";
  }

  int main() {
      std::thread t1(print_shared_data, 1);
      std::thread t2(print_shared_data, 2);
      
      t1.join();
      t2.join();
      
      return 0;
  }
  ```

- `std::unique_lock` is similar to `std::lock_guard`, but it provides more flexibility, allowing the mutex to be locked and unlocked manually. It is useful when you need to lock/unlock the mutex multiple times within a scope.

```cpp
#include <iostream>
#include <thread>
#include <mutex>

std::mutex mtx;  // Mutex to protect shared resource

void print_shared_data(int i) {
    std::unique_lock<std::mutex> lock(mtx);  // Locks the mutex
    std::cout << "Thread " << i << " is accessing shared data.\n";
    lock.unlock();  // Unlocks manually
}

int main() {
    std::thread t1(print_shared_data, 1);
    std::thread t2(print_shared_data, 2);
    
    t1.join();
    t2.join();
    
    return 0;
}
```

- `std::condition_variable` allows threads to wait for a certain condition to be met before proceeding. It's often used in scenarios where one thread needs to wait for another thread to update a shared resource.

```cpp
#include <iostream>
#include <thread>
#include <mutex>
#include <condition_variable>

std::mutex mtx;
std::condition_variable cv;
bool ready = false;  // Shared condition

void print_data(int i) {
    std::unique_lock<std::mutex> lock(mtx);
    while (!ready) {
        cv.wait(lock);  // Wait until the condition becomes true
    }
    std::cout << "Thread " << i << " is printing data.\n";
}

void go() {
    std::this_thread::sleep_for(std::chrono::seconds(1));  // Simulate work
    {
        std::lock_guard<std::mutex> lock(mtx);
        ready = true;
    }
    cv.notify_all();  // Notify all waiting threads
}

int main() {
    std::thread t1(print_data, 1);
    std::thread t2(print_data, 2);
    
    go();  // Notify threads to start
    t1.join();
    t2.join();
    
    return 0;
}
```

- `std::atomic` ensures that its value is updated in a way that guarantees that no other thread can interfere with the operation. It's useful for simple data types like integers and booleans where atomic operations are necessary.
  - `std::atomic` provides operations like `load()`, `store()`, `exchange()`, and `compare_exchange_strong()` that ensure atomicity without using locks.

```cpp
#include <iostream>
#include <thread>
#include <atomic>

std::atomic<int> counter(0);

void increment() {
    for (int i = 0; i < 100; ++i) {
        counter.fetch_add(1, std::memory_order_relaxed);  // Atomically increments
    }
}

int main() {
    std::thread t1(increment);
    std::thread t2(increment);
    
    t1.join();
    t2.join();
    
    std::cout << "Final counter value: " << counter.load() << std::endl; // 200
    
    return 0;
}
```

- Read-Write Locks (std::shared_mutex): when you have scenarios where multiple thread can read the data simultaneously, but only thread can write it at a time, a read-write lock can be useful. It allows multiple readers but ensures exclusive access for writers.
  - `std::shared_mutex` allows multiple threads to hold a shared lock for reading, but only one thread can hold an exclusive lock for writing.

```cpp
#include <iostream>
#include <thread>
#include <shared_mutex>

std::shared_mutex rw_mutex;
int shared_data = 0;

void read_data(int id) {
    std::shared_lock<std::shared_mutex> lock(rw_mutex);  // Shared read lock
    std::cout << "Thread " << id << " is reading shared data: " << shared_data << "\n";
}

void write_data(int value) {
    std::unique_lock<std::shared_mutex> lock(rw_mutex);  // Exclusive write lock
    shared_data = value;
    std::cout << "Writing new value: " << shared_data << "\n";
}

int main() {
    std::thread t1(read_data, 1);
    std::thread t2(read_data, 2);
    std::thread t3(write_data, 10);

    t1.join();
    t2.join();
    t3.join();

    return 0;
}
```

When to Use Which?

- Mutexes (`std::mutex`, `std::lock_guard`) are useful for general locking when accessing shared resources.
- Condition Variables (`std::condition_variable`) are useful for thread synchronization based on specific conditions (e.g., when a task is done, or a specific event happens).
- Atomic Variables (`std::atomic`) are ideal for simple, low-level synchronization with minimal overhead.
- Read-Write Locks (`std::shared_mutex`) are useful when multiple threads need to read from shared without interference, but exclusive write access is needed.

### 4. What is the difference between a mutex and a semaphore?

- Mutex (Mutual Exclusion)
  - Purpose: A mutex is used to ensure that only one thread can access a critical section of code at a time.
  - Behavior:
    - When a thread locks a mutex, no other thread can lock it until the mutex is unlocked by the owning thead.
    - It's typically used for exclusive access to a resource, where only one thread should modify or read shared data at a time.
    - The thread that locks the mutex must be the one that unlocks it.
  - Key Characteristics:
    - Only one thread can hold the mutex at any given time
    - It prevents race conditions by ensuring mutual exclusion
    - Can be use to protect shared resources like variables or objects from concurrent access

- Semaphore
  - Purpose: A semphore is used to manage access to a shared resource that can be accessed by multiple threads, but with a limit on how many threads can access it at the same time.
  - Behaviour:
    - A semaphore maintains a count (usually initialized to a specific value), which represents the number of threads that can simultaneously access the critical section.
    - Threads that attempt to acquire the sempahore will either succeed or block based on the current count.
    - Binary semaphores are sometimes used like mutexes, where the count is either 0 or 1, but semaphores in general are more flexible than mutexes in terms of controlling concurrency.
  - Key Characteristics:
    - A semaphore can allow more than one thread to access a shared resource at once, based on its count.
    - The count decreases when a thread acquires it and increases when a thread releases it.
    - Can be used for signaling or controlling concurrency (e.g., limiting the number of threads allowed to access a database connection).

### 5. What is a deadlock?

A deadlock occurs when two or more threads are stuck waiting for each other to release resources or complete actions, causing them to be unable to proceed. This results in a situation where no thread can make progress because they are all waiting indefinitely for each other to release resources.

For a deadlock to happen, all of the following four conditions must be true (known as the Coffman conditions):

- Mutual Exclusion: At least one resource must be held in a non-shareable mode, meaning only one thread can hold the resource at a time.
- Hold and Wait: A thread holding at least one resource is waiting to acquire additional resources held by other threads.
- No Preemption: Resources cannot be forcible taken away from threads holding them; they must release the resources voluntarily.
- Circular Wait: A set of threads must exist such that each thread is waiting for a resource that the next thread in the cycle holds.

Example of Deadlock: Consider two threads trying to acquire two lock in a different order:

1. Thread A locks Resource 1 and waits for Resource 2
2. Thread B locks Resource 2 and waits for Resource 1

How to Avoid Deadlocks:

- Lock Ordering: always acquire resources in the same order to prevent circular waiting: Always acquire Resource 1 before Resource 2 in every thread.
- Timeouts: Implement timeours for acquiring locks. If a thread cannoq acquire all the resources it needs within a specified time, it releases any held resources and retries.
- Deadlock Detection: Periodically check for deadlocks in the system and take corrective actions, like aborting or restarting threads involved in deadlocks.
- Resource Hierarchy: Use a hierarchy for acquiring resources. A thread must acquire resources in a predefined order and release them when done.

### 7. Is C++ thread-safe?

C++ itself is not thread-safe by default. This means that the language does not automatically handle the complexities of concurrent access to shared data or resources.

However, C++ provides tools and features (like mutexes, locks, and atomic operations) to help developers make their programs thread-safe. When multiple threads access shared data, you need to use synchronization mechanisms to ensure that they don't interfere with each other, which could lead to race conditions, deadlocks, or data corruption.

### 8. What is race condition and how to avoid race conditions??

A race condition occurs when multiple threads access shared data or resources concurrently, and the final outcome depends on the non-deterministic order of thread execution. This can lead to unexpected and incorrect behavior because threads can interfere with each other while reading from or writing to shared variables or resources.

To resolve race conditions, synchronization mechanisms are used to ensure that only one thread accesses the critical section at a time: Mutexes, Locks, Atomic Operations.

In short, a race condition happens when threads execute in an unpredictable order, leading to issues. Proper synchronization, such as using mutexes or atomic operations, ensures threads cooperate safely and avoid corrupting shared data.

### 9. What is an atomic operation?

An atomic operation is an operation that completes in a single step relative to other threads. It is guaranteed to be thread-safe, meaning that no other thread can observe the operation in an incomplete or inconsistent state. Atomic operations do not require locks and are usually supported by the hardware, ensuring that the operation happens as a single, indivisible action.

Key Characteristics of Atomic Operations:

- Indivisible: the operation cannot be interrupted by another thread. Once the operation starts, it will complete without any other thread being able to intervene.
- Thread-Safe: multiple threads can perform atomic operations on the same data without causing race conditions.
- Efficient: Atomic operations are typically faster than using locks (mutexes), as they avoid the overhead associated with acquiring and releasing locks.

```cpp
#include <atomic>
std::atomic<int> x(0);

// Atomic increment
x.fetch_add(1);

// Atomic compare-and-swap
x.compare_exchange_strong(expected_value, new_value);
```
