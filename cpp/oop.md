# OOP

> **Why OOP?**

* OOP paradigm is mainly useful for relatively big software software.
* The main advantage of OOP is better manageable code that real-world.

> **Class & Object**

* Class is a user-defined data type which holds its own data members and member functions.

* Object is an instance of class.

* When a class is defined, no memory is allocated but when it is instantiated (an object is created) memory is allocated.

  ```c++
  class Foo { ... }; // define a class
  Foo foo;           // declare an object 
  ```

> **What are main features of OOP?**

1. Encapsulation
2. Inheritance
3. Polymorphisim

> **What is Encapsulation?**

* It provides data hiding via accessor keywords such as private, protected, and public and bundling of data and methods together.

> **What is Inheritance?**

* A class is based on another class and uses data and implementation of the other class.

* The purpose of inheritance is code-reuse.

* "is-a" relationship.

* It's important to understand that inheritance works in only one direction. The base class doesn't know anything about the derived class.

* A pointer or reference to a base object can refer to its derived classes. However, you cannot call methods from the derived class through the base pointer or reference.

  ```c++
  class Base {
  public:
      void baseMethod();
  };
  
  class Derived : public Base {
  public:
      void derivedMethod();
  };
  
  Base base;
  base.derivedMethod(); // error
  
  Base *base = new Derived();
  base->derivedMethod(); // error
  ```

* If you want to prevent the inheritance, you have to mark a class as *final* keyword. 

* It means trying to inherit from it will result in a compilation error.

  ```c++
  class Base final {};
  class Derived : public Base {} // error
  ```

> **Pointer & Reference Type Compatibility**

* A reference or pointer to a base class can refer to a derived class object without using an explicit type cast.

  ```c++
  Derived d;
  Base *pb = &d; // ok
  Base &rb = &d; // ok
  ```

* Converting a derived-class reference or pointer to a base class reference or pointer is called *upcasting* and it is always allowed for public inheritance without the need for an explicit type cast.

  ```c++
  Derived d;
  Base *b = &d;
  Base &b = d;
  ```

* Converting a base class pointer or reference to a derived class pointer or reference is called *downcasting* and it is not allowed without an explicit type cast.

  ```c++
  Base *b = new Derived;
  Derived *d = dynamic_cast<Derived *>(b);
  ```

> **What is Object Composition?**

* Object composition is an alternative to class inheritance.
* New functionality is obtained by assembling or composing objects to get more complex functionality.

> **What is Polymorphism?**

* It means that objects behave differently in different contexts.
* In C++, we have two types of polymorphism: Compile-time and run-time.

1. Compile-time Polymorphism
   * This is also known as static or early binding.
   * Supported by templates, function/operator overloading and default arguments.
2. Run-time Polymorphism
   * This is also known as dynamic or late binding.
   * Supported by virtual functions and inheritance.

> **What is virtual keyword?**

* It provides run-time polymorphism.

* Resolved at run-time, compiler determines the type of the object at runtime and call appropriate function.

  ```c++
  class Animal {
  public:
      virtual void foo();
  };
  
  class Dog {
  public:
      void foo() override;
  };
  
  Animal *obj = new Dog();
  obj->foo(); // call Dog's foo
  ```

> **What is Overriding Methods?**

* The main reasons to inherit from a class are to add or replace functionality.

* In many cases, you will want to modify the behavior of a class by replacing or overriding method.

* To override a method, you redeclare it in the derived class definition exactly as it was declared in the base class and you add the override keyword. In the derived classes implementation file, you provide the new definition.

* A pointer or reference can refer to an object of a class or any of its derived classes. For example, if you have a base reference that refers to an object that is really a derived class.

* Using *override* keyword is highly recommended. Sometimes, it is possible to accidentally create a new virtual method instead of overriding a method from the base class.

  ```c++
  class Base {
  public:
      virtual void someMethod(double);
  };
  
  class Derived : public Base {
  public:
      virtual void someMethod(int); // not overriding method, calls base class
      void someMethod(int) override; // compiler warns for different argument type 
  }
  ```

* *Hiding Instead of Overriding:* Attempting to override a non-virtual method hides the base class definition and it will only be used in the context of the derived class.

  ```c++
  class Base {
  public:
    void go();  
  };
  
  class Derived : public Base {
  public:
      void go(); // omit virtual keyword
  };
  
  Derived obj;
  obj.go(); // calls derived's method
  
  Derived obj;
  Base &ref = obj;
  ref.go(); // calls base method because it's not virtual no overriden
  ```

> **How virtual functions works?**

* When a class is compiled in C++, a binary object is created that contains all methods for the class. In the non-virtual case, the code to transfer control to the appropriate method is hard-coded directly where the method is called based on the compile-time type. This is called static or early binding.

* If the method is declared virtual, the correct implementation is called through the use of a special area of memory called the vtable. Each class that has one or more virtual methods, has a vtable, and every object of such a class contains a pointer to said vtable. This vtable contains pointers to the implementations of the virtual methods. In this way, when a method is called on an object, the pointer is followed into the vtable and the appropriate version of the method is executed based on the actual type of the object at run time. This is called dynamic binding or late binding.

  ```c++
  class Base {
  public:
      virtual void func1();
      virtual void func2();
      vod nonVirtualFunc();
  };
  
  class Derived : public Base {
  public:
      virtual void func2() override;
      void nonVirtualFunc();
  };
  
  Base base;
  Derived derived;
  ```

  The base object contains a pointer to its vtable. This vtable has two entries, one for func1() and one for func2().

  The derived object also contains a pointer to its vtable, which has two entries, one for func1() and one for func2(). Its func1() entry points to Base::func1() because derived does not override func1(). On the other hand, its func2() entry points to Derived::func2(). Vtable do not contain any entry for the nonVirtualFunc() method because that method is not virtual.

  ```c++
  Base::vtable    -> Base::func1, Base::func2
  Derived::vtable -> Base::func1, Derived::func2
  ```

  1. An object of a base class contains a pointer to a table of addresses of all the virtual functions for that class.
  2. An object of a derived class contains a pointer to a separate table of addresses.
  3. If the derived class provides a new definition of a virtual function, the vtable holds the address of the new function.
  4. If the derived class doesn't redefine the virtual function, the vtable holds the address of the original version of the function.
  5. If the derived class defines a new function and makes it virtual, its address is added to the vtable.
  6. When you call a virtual function, the program looks at the vtable address stored in an object and goes to the corresponding table of function addresses.
  7. If you use the first virtual function defined in the class declaration, the program uses the first function address in the array and executes the function that has the address and so on.

*Drawbacks*

* Each object has its size increased by the amount needed to hold an address.
* For each class, the compiler creates a table (an array) of address of virtual functions.
* For each function call, there's an extra step of going to a table to look up an address.

*Notes*

* Beginning a class method declaration with keyword virtual in a base class makes the function virtual for the base class and all classes derived from the base class, including classes derived from the derived classes, and so on.

> **Why Two Kinds of Binding and Why static is the default?**

* There are two reasons: efficiency and a conceptual model.
* For a program to be able to make a runtime decision, it has to have some way to keep track of what sort of object a base class pointer or reference to, and some extra processing overhead.
* Another reason, you design a class that won't be used as a base class for inheritance, you don't need dynamic binding.
* Static binding is more efficient is the reason it is the default choice for C++. In C++, "You shouldn't have to pay for features you don't use."

> **Virtual Destructor?**

* It is usually required in a base class. Whenever upcasting is done, destructors of the base class must be made virtual for proper destruction of the object when the program exists.

  ```c++
  Base *b = new Derived; // upcasting, no virtual dtor
  delete b;			   // just call base, not safe maybe memory leak
  
  Base *b = new Derived; // upcasting, base with virtual dtor
  delete b;			   // call first derived dtor then base dtor
  ```

  

> **What is Abstraction?**

* It is the concept that separating the interface from the implementation.
* Supported by pure virtual functions.
* Redefined in a derived classes.
* At least one pure virtual function is must.
* Not instantiate abstract classes.