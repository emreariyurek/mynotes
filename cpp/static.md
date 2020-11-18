# static

Static elements are allocated storage only once in a program lifetime in static storage area. And they have a scope till the program lifetime. 

* The static keyword can be used to declare variables and functions at global scope, namespace scope, and class scope. Static variables can also declared at local scope.
* Static duration means that the object or variable is allocated when the program starts and is deallocated when the program ends.
* External linkage means that the name of the variable is visible from outside the file in which the variable is declared. 
* Internal linkage means that the name is not visible outside the file in which the variable is declared. 
* By default, an object or variable that is defined in the global namespace has static duration and external linkage.
* Starting in C++11, a static local variable initialization is guaranteed to be thread-safe. 
* It can be used in various ways:
  1. Static variables in functions
  2. Static class objects
  3. Static member variable in class
  4. Static member function in class

> **1. Static Variables in Functions**

* Static variables when used inside function are initialized only once, and then they hold there value even through function calls.

* These static variables are stored on static storage area, not in stack.

  ```c++
  void counter() {
      static int count = 0;
      cout << count++ << endl;
  }
  
  int main()
  {
      for (int i = 0; i < 5; i++) {
          counter();
      }
  }
  
  // output: 0, 1, 2, 3, 4
  ```

  If we do not use static keyword, the variable count, is reinitialized every time when counter() function is called, and gets destroyed each time when counter() functions ends. But, if we make it static, once initialized count will have a scope till the end of main() function and it will carry its values through function calls too.

  If you don't initialize a static variable, they are by default initialized to zero.

> **2. Static Class Objects**

* Static keyword works in the same way for class objects too.

* Objects declared static are allocated storage in static storage area, and have scope till the end of program.

* Static objects are also initialized using constructors like other normal objects. Assignment to zero, on using static keyword is only for primitive data types, not for user defined data types.

  ```c++
  class MyClass {
  public:
  	MyClass() {
  		i = 0;
          cout << "ctor" << endl;
  	}
      
      ~MyClass() { cout << "dtor" << endl; }
  
  private:
      int i;
  };
  
  void f() {
      static MyClass obj;
  }
  
  int main()
  {
      f();
      cout << "terminate main function" << endl;
  }
  
  // output: ctor, terminate main function, dtor
  ```

  You must be thinking, why was the destructor not called upon the end of the scope of if condition, where the reference of object obj should get destroyed. This is because object was static, which has scope till the program's lifetime, hence destructor for this object was called when main() function exits.

> **3. Static Data Members in Class**

* They are not associated with any object and shared by all the objects. 

* They exists even if no objects of the class have been defined.

* There is only one instance of them in the entire program with static duration.

* Static data members are not initialized using constructor, because these are not dependent on object initialization. It must be initialized explicitly, always outside the class. If not initialized, linker will give error.

  ```c++
  class MyClass {
  public:
      static int i;
  };
  
  int MyClass::i = 1;
  ```

* They cannot be mutable.

* If a static data member of integral or enumeration type is declared const, it can be initialized with an initializer in which every expression is a constant expression.

  ```c++
  struct X {
      const static int n = 1; // ok
      const static int m{2}; // ok
      const static int k;
  };
  
  const int X::k = 3;
  ```

* If a static data member of LiteralType is declared constexpr, it must be initialized with an initializer in which every expression is a constant expression.

  ```c++
  struct X {
  	constexpr static int arr[] = {1, 2, 3};	// ok
  	constexpr static std::complex<double> n = {1, 2}; // ok
  	constexpr static int k;  // error: constexpr static requires an initializer
  };
  ```

> **4. Static Member Functions**

* They are not associated with any object.
* They have no "this" pointer.
* They cannot access ordinary data members and member functions, but only static data members and static member functions.
* They cannot be virtual or const.
* The address of a static member function may be stored in a regular pointer to function, but not in a pointer to member function.