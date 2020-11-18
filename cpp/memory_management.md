# Memory Management

* Memory allocation and management is a particularly error-prone area of C++.
* To write high-quality C++ programs, professional C++ programmers need to understand how to memory works behind the scenes.
* However, in modern C++ you should avoid low-level memory operations as much as possible.
* For example, instead of dynamically allocated C-style arrays, you should use std containers, such as vector, which handle all memory management automatically for you.
* Instead of raw pointers, you should use smart pointers, such as unique_ptr and shared_ptr, which automatically free the underlying resource, such as memory, when it's not needed any more.
* Basically, you should try to avoid having calls to memory allocation routines such as new / new[] and delete / delete[] in your code.

> **Memory Layout**

* A typical memory representation of a program consists of  5 sections.

1. **Text Segment**

   * A text segment, also known as a code segment or simply as text, is one of the sections of a program in an object file or in memory, which contains executable instructions.
   * Usually, the text segment is sharable so that only a single copy needs to be in memory for frequently executed programs, such as text editors, the compiler, the shells, and so on.
   * Text segment is often read-only, to prevent a program from accidentally modifying its instructions.

2. **Initialized Data Segment**

   * Initialized data segment, usually called simple data segment. 

   * This segment can be further classified into initialized read-only area and initialized read-write area.

   * Data segment is not read-only, since the values of the variables can be altered at run time.

     ```c++
     static int i = 10; // stored in data segment
     global int i2 = 10; // stored in data segment
     char s[] = "Hello World"; // stored in data segment read-write area
     const char *s = "Hello World"; // stored in data segment read-only area
     ```

3. **Uninitialized Data Segment**

   * Uninitialized data segment often calls the "bss" segment.

   * It contains all global and static variables.

   * Data in this segment is initialized by 0 before the program starts executing.

     ```c++
     static int i; // stored in bss, equal to 0
     global int i2; // stored in bss, equal to 0
     ```

4. **Stack**

   * Automatic variable is allocated on the stack. It is automatically deallocated when the program flow leaves the scope which the variable is dead.

     ```c++
     void foo() {
         int i = 10; // allocated on the stack
     }
     ```

5. **Heap**

   * It is dynamic memory allocation segment.

   * When you use the new keyword, memory is allocated on the heap. The variable ptr is on the stack but points to memory on the heap.

     ```c++
     int *ptr = new int;
     ```

> **malloc vs new**

* malloc is a function, new is a operator.
* new doesn't just allocate memory, it constructs objects.
* A similar difference exists between the free() function and delete operator. With free(), the object's destructor is not called. With delete, the destructor is called and the object is properly cleaned up.

> **Dynamic Arrays**

* Always use delete on anything allocated with new, and always use delete[] on anything allocated with new[].

  ```c++
  int *arr = new int[5];
  delete[] arr;
  arr = nullptr;
  
  class Simple {};
  Simple *simples = new Simple[4];
  delete[] simples;
  simples = nullptr;
  ```

> **Smart Pointers**

* Sometimes you might think that your code is properly deallocating dynamically allocated memory. Unfortunately, it most likely is not correct in all situations.

  ```c++
  void leaky() {
      Simple *ptr = new Simple();
      ptr->go();
      delete ptr;
  }
  ```

  This function dynamically allocates a Simple object, uses the object, and then properly calls delete. However, you can still have memory leaks in this example! If the go() method throws an exception, the call to delete is never executed, causing a memory leak.

* Smart pointers help you manage your dynamically allocated memory and are the recommended technique for avoiding memory leaks.

* There are two types of smart pointers: unique_ptr and shared_ptr.

* As a rule of thumb, default smart pointer should be unique_ptr. Only use shared_ptr when you really need to share the resource.

1. **unique_ptr**

   * It takes unique ownership of the resource and when it goes out of scope or is reset, it frees the referenced source.

   * The get() method can be used to get direct access to the underlying pointer.

     ```c++
     void processData(Simple *simple) {}
     
     auto ptr = make_unique<Simple>();
     processData(ptr.get());
     ```

   * You can free the underlying pointer of a unique_ptr and optionally change it to another pointer using reset.

     ```c++
     ptr.reset(); // free resource and set to nullptr
     ptr.reset(new Simple()); // free resource and set to new instance
     ```

   * You can disconnect the underlying pointer from a unique_ptr with release(). The release() method returns the underlying pointer to the resource and then sets the smart pointer to nullptr.

     ```c++
     Simple *simple = ptr.release(); // release ownership
     ...
     delete simple;
     simple = nullptr;
     ```

   * unique_ptr cannot be copied because it represents the unique ownership but it is possible to use with move semantics.

2. **shared_ptr**

   * It is a reference counting ownership model. 
   * The counter is incremented each time a new pointer points to the resource and decrement when destructor of object is called.
   * When the reference count drops to zero, there are no owners of the resource anymore, so it will be destroyed.
   * We should use shared_ptr when we really need to share the resource.