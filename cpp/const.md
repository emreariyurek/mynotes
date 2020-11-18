# const

Constant is something that doesn't change. When modifying a data declaration, the const keyword specifies that the object or variable is not modifiable. It can be used with:

1. Variables
2. Pointers 
3. Function Arguments and Return Types 
4. Class Data Members 
5. Class Member Functions
6. Class Objects

> **1. Variables**

* If you make any variable as constant, using const keyword, you cannot change its value. If we try to change its value, we will get compile time error.

* Constant variables must be initialized while they are declared.

```c++
int main()
{
	const int i = 10;
    const int j = i + 10; // works fine
    i++; // this leads to compile error
}
```

> **2. Pointers**

* Read from "right to left" rule:

  ```c++
  1. const int *ptr; // ptr is a pointer to constant int
  - cannot change its value but can modify its address
      const int *ptr = &a;
  	*ptr = 5; // error
  	ptr++;    // ok
      
  2. int *const ptr; // ptr is a constant pointer to int
  - cannot change its address but can modify its value
      int *const ptr = &a;
  	*ptr = 5; // ok
      ptr++;    // error
  ```

> **3. Function Arguments and Return Types**

* We can make the arguments or return type of a function as const. Then we cannot change any of them. 

  ```c++
  void f(const int i) { i++; // error }
  const int g() { return 1; }
  ```

* For built-in datatypes, returning a const or non-const value, doesn't make any difference.
* For user defined datatypes, returning const, will prevent its modification.
* Temporary objects created while program execution are always of const type.
* If a function has a non-const parameter, it cannot be passed a const argument while making a call.
* But, a function which has a const type parameter, can be passed a const type argument as well as a non-const argument.

> **4. Class Data Members**

* They initialize in-class definition or constructor member initializer list.

* Once initialized, its value cannot be changed.

  ```c++
  class Foo {
  public:
  	Foo() : a(1) {
          b = 30; // error
      }
      
  private:
      const int a;
      const int b = 10;
  };
  ```

> **5. Class Member Functions**

* Declaring a member function with the const keyword specifies that the function is a "read-only" function.

* A const member function cannot modify any non-static data members. 

* A const member function cannot call any non-const member functions.

  ```c++
  class Foo {
  public:
      int barConst() const;
      int barNonConst();
      
      int func() const {
          x = 100 // error that cannot modify any data members
          barNonConst() // error
          barConst() // ok
      }
     
  private:
      int x = 10;
  };
  ```

* A const member function can be called by any type of object. Non-const functions can only be called by non-const objects.

  ```c++
  class Foo {
  public:
      void foo() const;
      void bar();
  };
  
  int main()
  {
      const Foo f1;
      f1.foo(); // ok
      f1.bar(); // error
      
      Foo f2;
      f2.foo(); // ok
      f2.bar(); // ok
  }
  ```

> **6. Class Objects**

* When an object is declared or created using the const, its data members can never be changed, during the object's lifetime.

  ```c++
  class Foo {
  public:
  	int x = 10;
  };
  
  int main()
  {
  	const Foo f;
  	f.x = 20; // error
  }
  ```

  