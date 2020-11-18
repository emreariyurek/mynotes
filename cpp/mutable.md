# mutable

It is used in two ways:

1. Mutable Data Members
2. Mutable Lambda Expressions

> **1. Mutable Data Members**

* It is used with non-static and non-const member variables of class which we want to change even if the object is declared const. 

  ```c++
  class Foo {
  public:
      bool getFlag() const {
      	m_count++; // ok with mutable
          return m_flag;
      }
      
  private:
      bool m_flag;
      mutable int m_count;
  };
  ```

  ```c++
  class Foo {
  public:
      mutable int x = 4;
      int y = 5;
  };
  
  int main()
  {
      const Foo f;
      f.x = 10; // ok with mutable
      f.y = 11; // error
  }
  ```

> **2. Mutable Lambda Expressions**

* There is another use for mutable is with lambda declaration that removes const qualification from parameters captured by copy. Generally, the function call operator of a closure is const and cannot modify any members captured by value.

  ```c++
  int main()
  {
      int i = 2;
      auto err = [i]() { i++; } //error, trying to modify const i
  	auto ok = [i]() mutable { i++; } // ok
  }
  ```

  

