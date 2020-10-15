# SOLID Principles

SOLID is an acronym for five design principles intended to make software designs more understandable, flexible, and maintainable.

> **Single Responsibility Principle**

*A class should have only one reason to change.*

A class should take care of only one responsibility.

This means that a class should not be loaded with multiple responsibilities and a single responsibility should not be spread across multiple classes or mixed with other responsibilities.

The reason is that the more changes requested in the future, the more changes the class needs to apply.

> **Open Closed Principle**

*Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.*

Modification means changing the code of an existing class, and extension means adding new functionality.

So what this principle wants to say is: We should be able to add new functionality without touching the existing code for the class.  This is because whenever we modify the existing code, we are taking the risk of creating potential bugs. 

But how are we going to add new functionality without touching the class, you may ask. It is usually done with the help of interfaces and abstract classes.

> **Liskov Substitution Principle**

A parent class object should be able to refer child objects seamlessly during runtime polymorphism.

It states that subclasses should be substitutable for their base classes.

This means that, given that class B is a subclass of class A, we should be able to pass an object of class B to any method that expects an object of class A and the method should not give any weird output in that case.

This is the expected behavior, because when we use inheritance we assume that the child class inherits everything that the superclass has. The child class extends the behavior but never narrows it down.

> **Interface Segregation Principle**

Client should not be forced to use an interface if it does not need it.

Segregation means keeping things separated, and this principle is about separating the interfaces.

The principle states that many client-specific interfaces are better than one general-purpose interface. Clients should not be forced to implement a function they do no need.

```c++
class ParkingLot {
public:
	ParkingLot();
	
	virtual void parkCar(); // decrease empty spot count by 1
	virtual void unpackCar(); // increase empty spots by 1
	virtual int getCapacity() const; // returns car capacity
	virtual double calculateFee(Car car) const; // returns the price based on number of hours
	virtual void doPayment(Car car);
};
```

We modeled a very simplified parking lot. It is the type of parking lot where you pay an hourly fee. Now consider that we want to implement a parking lot that is free.

```c++
class FreeParking : public ParkingLot {
public:
	void parkCar() {}
	void unparkCar() {}
	int getCapacity() const {}
	double calculateFee(Car car) { return 0; }
	void doPayment(Car car) { // nothing }
};
```

Our parking lot interface was composed of 2 things: Parking related logic (park car, unpark car, get capacity etc.) and payment related logic.

But it is too specific. Because of that, our FreeParking class was forced to implement payment-related methods that are irrelevant. Let's separate the interfaces.

1. ParkingLot
   * FreeParkingLot
   * PaidParkingLot
     * HourlyFeeParkingLot
     * ConstantFeeParkingLot

We've now separated the parking lot. With this new model, we can even go further and split the PaidParkingLot to support different types of payment.

Now our model is much more flexible, extandable, and the clients do not need to implement any irrelevant logic because we provide only parking-related functionality in the parking lot interface.

> **Dependency Inversion Principle**

*High-level modules should not depend on low-level modules. Bot should depend on abstractions.*

*Abstractions should not depend on details. Details should depend on abstractions.*

