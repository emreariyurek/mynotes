# Design Patterns

> **What are Design Patterns?**

* Design patterns represent the best practices used by experienced object-oriented software developers. 

* Design patterns are solutions to general problems that software developers faced during software development. These solutions were obtained by trial and error by numerous software developers over quite a substantial period of time.

* Design patterns are classified as three groups.
  1. Creational Patterns
  2. Structural Patterns
  3. Behavioral Patterns

# 1. Creational Patterns

These design patterns provide a way to create objects while hiding the creation logic, rather than instantiating objects directly using new operator. This gives program more flexibility in deciding which objects need to be created for a given use case.

> **Abstract Factory**

Provide an interface for creating families of related or dependent objects without specifying their concrete classes.

> **Factory Method**

Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses like virtual constructor.

![](C:\Users\tr1a5117\Desktop\factory.gif)

> **Participants**

* **Product (Document)**
  * defines the interface of objects the factory method creates
* **ConcreteProduct (MyDocument) **
  * implements the Product interface
* **Creator (Application) **
  * declares the factory method, which returns an object of type Product. Creator may also define a default implementation of the factory method that returns a default ConcreteProduct object
  * may call the factory method to create a Product object
* **ConcreteCreator (MyApplication) **
  * overrides the factory method to return an instance of a ConcreteProduct

> **Implementation**

1. **An ordinary function** with if-else statements which returns an instance of a set of derived classes according to some input.
   * Disadvantage: Adding new derived classes
2. **A static method** with if-else statements. 
   * Disadvantage: Requires modifying the code when new classes are added to the hierarchy.
3. **Registry-based factory** (mostly known as Polymorphic Factory) - A class contains a factory method for instantiating derived classes based on some input and hash-table for registration of derived classes.

> **Difference between Factory Method and Abstract Factory**

* Factory Method is used to **create one product** only but Abstract Factory is about **creating families of related or dependent products**.
* Factory Method depends on **inheritance** to decide which product to be created, while Abstract Factory, there's a separate class dedicated to create a family of related/dependent products and its (any concrete subclass factory) object can be passed to the client which uses it (**composition**).
* Factory Method is **just a method** while Abstract Factory is an **object**.
* Abstract Factory is one level **higher in abstraction** than Factory Method. Factory Method **abstracts the way objects are created,** while Abstract Factory also **abstracts the way factories are created** which in turn abstracts the way objects are created.
* As Abstract Factory is at a higher level in abstraction, it **often uses** Factory Method to create the products in factories.

> **Singleton**

Ensure a class only has one instance, and provide a global point of access to it.

# 2. Structural Patterns

> **Adapter**

Convert the interface of a class into another interface clients expects. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

> **Bridge**

Separates an object's abstraction from its implementation.

> **Decorator**

Add responsibilities to objects dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.

> **Facade**

A single class that represents an entire subsystem.

> **Proxy**

An object representing another object.

# 3. Behavioral Patterns

> **Mediator**

Defines simplified communication between classes.

> **Strategy**

Define a family of algorithm, encapsulate each one, and make them interchangeable. Strategy lets algorithm vary independently from clients that use it.

> **Template Method**

Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.

> **Observer**

Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

> **Visitor**

Defines a new operation to a class without change.