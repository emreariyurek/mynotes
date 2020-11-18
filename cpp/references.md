# References

* It is an alias, another name for an already existing variable.
* All modifications to the reference change the value of the variable to which it refers.

> **Advantages**

	1. Safer: since references must be initialized, wild references no exist
 	2. Easier to use: don't need dereferencing operator, using dot operator instead of arrow operator

> **Disadvantages**

1. Once a reference is created, it cannot be later made to reference another object
2. References cannot be null
3. A reference must be initialized when declared

> **1. Reference Variables**

* Reference variables must be initialized as soon as they are created.

* Usually, references are created when they are declared, but reference data members need to be initialized in the constructor initializer for the containing class.

  ```c++
  int x = 3;
  int &xref = x;
  xref = 10;
  int &xref2; // error
  ```

* You cannot create a reference to an unnamed value, such as integer literal, unless the reference is to a const value.

  ```c++
  int &ref1 = 5; // error
  const int &ref2 = 5; //ok
  ```

* The same holds for temporary objects. You cannot have a non-const reference to a temporary object, but a const reference is fine.

  ```c++
  string getString() { return "Hello World"; }
  
  string &str1 = getString(); // error
  const string &str2 = getString(); // ok
  ```

* A reference always refers to the same variable to which it is initialized, references cannot be changed once they are created.

* This rule leads to some confusing syntax. If you "assign" a variable to a reference when reference is declared, the reference refers to that variable.

* However, if you assign a variable to a reference after that, the variable to which the reference refers is changed to the value of the variable being assigned. The reference is not updated to refer to that variable.

  ```c++
  int x = 3;
  int y = 4;
  int &xref = x;
  xref = y; // changes value of x to 4. doesn't make xref refer to y
  
  int x = 3;
  int z = 5;
  int &xref = x;
  int &zref = z;
  zref = xref; // assigns values, not references
  ```

  The final line does not change zref. Instead, it sets the value of z to 3, because xref refers to x, which is 3.

* You cannot change the variable to which a reference refers after it is initialized, you can change only the value of that variable.

> **2. Reference Data Members**

* Data members of classes can be references.

* You must initialize reference data members in the constructor initializer, not in the body of the constructor.

  ```c++
  class MyClass {
  public:
      MyClass(int val) : ref(val) {}
  
  private:
      int ref;
  };
  ```

> **3. Pass-by-Reference vs Pass-by-Value**

* Pass-by-reference avoids copying the arguments to the function for efficiency.

> **4. Reference Return Values**

* You can also return a reference from a function. The main reason is efficiency.
* You can only use this technique if the object continues to exist following the function termination. Never return reference to a variable that is locally scoped because will be destroyed when the function ends.
* A second reason to return a reference is if you want to be able to assign to the return value directly as an lvalue. Several overloaded operators commonly return references.

> **5. RValue References**

* An rvalue is anything that is not an lvalue, such as constant value or a temporary object.

  ```c++
  void handleMessage(string &message) {
      cout << "handle message with lvalue reference: " << message << endl;
  }
  
  handleMessage("Hello World"); // error: a literal is not an lvalue
  string a = "Hello";
  string b = "World";
  handleMessage(a + b); // error: a temporary is not an lvalue
  ```

  