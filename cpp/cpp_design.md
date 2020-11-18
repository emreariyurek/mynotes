# CHAPTER 4: DESIGNING PROFESSIONAL C++ PROGRAMS

What's In This Chapter?

1. The definition of programming design
2. The importance of programming design
3. The aspects of design that are unique to C++
4. The two fundamental themes for effective C++ design: abstraction and reuse
5. The different types of code available for reuse
6. The advantages and disadvantages of code reuse
7. General strategies and guidelines for reusing code
8. Open-source libraries
9. The C++ Standard Library

Before writing a single line of code in your application, you should design your program. What data structures will you use? What classes will you write? This plan is especially important when you program in groups.

> **1. What is Programming Design?**

- The very first step when starting a new program, or a new feature for an existing program, is to analyze the requirements. 
- A vital outcome of this analysis phase is a functional requirements document describing what exactly the new piece of code has to do, but it does not explain how it has to do it. Requirement analysis can also result in a non-functional requirements document describing how the final system should be, compared to what it should do. Examples of non-functional requirements are that the system needs to be secure, extensible, satisfy certain performance criteria, and so on.
- Once all requirements have been collected, the design phase of the project can start. Informally, the design is how you plan to write the program. You should generally write your design in the form of a design document. Although every company or project has its own variation of a desired design document format, most design documents share the same general layout, which include two main parts:

  1. The gross subdivision of the program into subsystems, including interfaces and dependencies between the subsystems, data flow between the subsystems, input and output to and from each subsystem.
  2. The details of each subsystem, including subdivision into classes, class hierarchies, data structures, algorithms, etc.

- The design documents usually include diagrams and tables showing subsystem interactions and class hierarchies. The UML is the industry standard for that.

NOTE: The point of designing is to think about your program before you write it.

- Of course, it is inevitable that the design will need to be modified once you begin coding and you encounter issues that you didn't think of earlier. Software-engineering process have been designed to give you the flexibility to make these changes. Scrum, an agile software development methodology, is one example of such an iterative process whereby the application is developed in cycles, known as sprints. With each sprint, designs can be modified, and new requirements can be taken into account.

> **2. The Importance of Programming Design**

> **3. Designing for C++**

- It's important to remain aware of whether or not you are making real progress. If you find that you are stuck, you can take one of the following actions:

 * Ask for help. Consult a coworker, mentor, book, or web page.
 * Work on something else for a while. Come back to this design choice later.
 * Make a decision and move on. Even if it's no ideal solution, decide on something and try to work with it. An incorrect choice will soon become apparent. Sometimes, there is no clean way to accomplish and have to accept an "ugly" solution if it's the only realistic strategy to fullfill your requirements. Whatever you decided, make sure you document your decision, so that you and others in the future know why you made it.

NOTE: Keep in mind that good design is hard, and getting it right takes practice. Don't expect to become an expert overnight, and don't be surprised if you find it more difficult to master C++ design than C++ coding.

> **4. Two Rules for C++ Design**

- There are two fundamental design rules in C++: abstraction and reuse.

  4.1 **Abstraction**

  - The principle of abstraction is easiest to understand through a real-word analogy. For example, a television. We don't know, nor do care, how the tv works. We just interact with the tv through its interface: the power button, channel changer, volume control etc. So we can turn it on and off, change the channel, adjust the volume, and add external components.
  - The abstraction principle is similar in software. You can use code without knowing the underlying implementation. 
  - As a trivial example, your program can make a call to the sqrt() function declared in the header file <cmath> without knowing what algorithm the function actually uses to calculate the square root. In fact, the underlying implementation of the square root calculation could change between releases of the library, and the interface stays the same, your function call will still work.
  - Another example, cout. You don't need to understand how cout manages to display that text on the user's screen. You only need to know the public interface.

  4.2 **Reuse**

  - The second fundamental rule of desing in C++ is reuse. 
  - Do not reinvent the wheel every time.
  - You should design your programs so that you can reuse your classes, algorithms, and data structures. You and your coworkers should be able to use these components in both the current project and future projects. 

***
- Learning the C++ language and becoming a good C++ programmer are two very different things. If you sat down and read the C++ standard, memorizing every fact, you would know C++ as well as anybody else. However, until you gained some experience by looking at code and writing your own programs, you wouldn't necessarily be a good programmer. The reason is that the C++ syntax defines what the language can do but doesn't say anything about how each feature should be used. 
- Using design patterns is important. It's important for you to familiarize yourself with these patterns and techniques so that you can recognize when a particular design problem calls for one of these solutions.
***

> **5. Reusing Existing Code**

- Experienced C++ programmers never start a project from scratch. They incorporate code from a wide variety of sources, such as the Standard Library, open-source libraries, proprietary code bases in their workplace, and their own code from previous projects.
- You should reuse code liberally in your design. In order to make the most of this rule, you need to understand the types of code that you can reuse and the tradeoffs involved in code reuse. You should analyze the advantages and disadvantages of code reuse.

***

Reusing code does not mean copying and pasting existing code! In fact, it means quite the opposite: reusing code without duplicating it.

***

> **6. Deciding Whether or Not to Reuse Code** 

- There are some advantages and disadvantages of reusing code and make the decision about whether or not to reuse code. 
- Often, the decision is obvious. For example, if you want to write a GUI in C++, you should use a framework such as Qt. You don't waste time to learn OS specific library. 
- However, other times the choice is less obvious. For example, if you are unfamiliar with a library or framework, and need only a simple data structure, it might not be worth the time to learn the entire framework to reuse only one component that you could write in a few days.
- Ultimately, you need to make a decision based on your own particular needs. It often comes down to a tradeoff between the time it would take to write it yourself and the time required to find and learn how to use a library to solve the problem. Carefully consider how the advantages and disadvantages listed and decide which factors are most important to you.   

* Listed Advantages & Disadvantages
* Understand the Capabilities and Limitations
* Understand the Performance
* Understand Platform Limitations
* Understand Licensing and Support

>  **7. Designing a Programming**

* Requirements
  * Design Steps
    * Divide the Program into Subsystems 
    * Specify Class Hierarchies for Each Subsystem
    *  Specify Classes, Data Structures, Algorithms, and Patterns for Each Subsystem
    *  Specify Error Handling for Each Subsystem

> **8. Summary**

- This chapter involves two design themes. 
- The first theme, the concept of abstraction, or separating interface from implementation.
- The second theme, the notion of reuse, both of code and designs, also arises frequently in real-world projects. Your C++ designs should include both reuse of code, in the form of libraries and frameworks, and reuse of ideas and designs, in the form of techniques and patterns. You should write your code to be as reusable as possible. Also remember about the tradeoffs and about specific guidelines for reusing code, including understanding the capabilities and limitations, the performance, licensing and support models.

***

Things to Remember: Design is subjective. Be prepared to defend design decisions you make during the interview.

Q1: Tell me the steps in designing a good program?
A1: Focus on high-level aspects. Do not explain previous job. Explain the gathering requirements, where the libraries come into play, how to deal with that etc.

***

# CHAPTER 5: DESIGNING WITH OBJECTS

What's In This Chapter?

1. What object-oriented programming design is
2. How you can define relationships between different objects
3. The importance of abstraction and how to use it in your designs

1. The Object-Oriented Philosophy

-  Unlike the procedural approach -which is based on the question, What does this program do? the object-oriented approach asks another question: What real-world objects am I modelling? 
- OOP is based on the notion that you should divide your program not into tasks, but into models of physical objects such as classes, components, properties and behaviours.

> **1. What object-oriented programming design is**

1. **Classes**

   * A class helps distinguish an object from its definition.

   * An object is an instance of a class.

   * As a more concrete example, "stock quote" is a class because it defines the abstract notion of what makes up a quote. A specific quote, such as "Microsoft stock quote", would be an object because it is a particular instance of the class.

2. **Components**

   * A component is essentially the same thing as a class, just smaller and more specific.

   * A good object-oriented program might have an Airplane class, but this class would be huge if it fully described an airplane. Instead, the Airplane class deals with many smaller, more manageable, components. Each of these components might have further subcomponents. For example, the landing gear is a component of an airplane, and the wheel is a component of the landing gear.

3. **Properties**

   * Properties are the characteristics that describe an object.

   * You can also think about properties on the class level. Class properties are shared by all objects of a class, while object properties are present in all objects of the class, but with different values.

   * In the stock selection example, a stock quote has several object properties, including the name of the company, its ticker symbol, the current price, and other statistics.

4. **Behaviors**

   * Behaviors for classes are implemented in so-called class methods.

   * The stock selection example provides some more practical behaviors for example analyzing.

5. **Object Relationships**

   * There are two main types of object relationships: has-a and is-a relationship.

> **2. How you can define relationships between different objects**

1. **The Has-A Relationship**

   * Objects engaged in a has-a, or aggregation, relationship follow the pattern A has a B, or A contains a B.

   * Components, as defined earlier, generally represent a has-a relationship because they describe objects that are made up of other objects.

   * A real-world example, between a zoo and a monkey. You could say that a zoo has a monkey or a zoo contains a monkey. 

   * Another example is UI window that contains label, buttons etc.

2. **The Is-A Relationship (Inheritance)**

   * The is-a relationship is such a fundamental concept of object-oriented programming that is has many names, including deriving, subclassing, extending, and inheriting. 

   * Fundamentally, inheritance follows the pattern A is a B or A is really quite a bit like B.

   * A monkey is an animal. Similarly, a giraffe is an animal, a kangaroo is an animal. 

   * A checkbox extends the Button class by adding state whether the box is checked or unchecked.

   * When relating classes in an is-a relationship, one goal is to factor common functionality into the base class, the class that other classes extend. 

   Inheritance Techniques:

   1. Adding functionality (add function in derived class)

   2. Replacing functionality (override function of base class)

- The Fine Line between Has-A and Is-A: Which solution is right? There's no clear answer.
- If you do have a choice between the two types of relationships, I recommend, prefer has-a relationship instead is-a relationship.

  **Hierarchies**

  1. Organizes classes into meaningful functional relationships
  2. Supports code reuse by factoring common functionality to base classes

  3. Avoids having derived classes that override much of the parent's functionality, unless the parent is an abstract class.

3. **Multiple Inheritance**

   * A class can have more than one base class such as PictureButton inherits from Button and Image.

   * Multiple inheritance can be very useful in certain cases, but it also has a number of disadvantages that you should always keep in mind.

4. **Mixin Classes**

   * Mixin classes represent another type of relationship between classes.

   * In C++, a mixin class is implemented syntactically just like multiple inheritance, but the semantics are refreshingly different.

   * A mixin class answers the question, "What else is this class able to do?" and the answer often ends with "-able". They are a way that you can add functionality to class without commiting to a full is-a relationship. You can think of it as a shares with relationship. 

   * Mixin classes are used frequently in user interfaces. Instead of saying that a PictureButton class is both an Image and a Button, you might say that it's an Image that is Clickable. A folder icon on your desktop could be an Image that is Draggable and Clickable.

   * In general, mixin classes are easier to digest than multiple inheritance because they are very limited in scope. The Clickable mixin class might just add "mouse down" and "mouse up" behaviors. 

5. **Abstraction**

> **3. The importance of abstraction and how to use it in your designs**

1. **Interface versus Implementation**

   * The key to abstraction is effectively separating the interface from the implementation. 

   * The implementation is the code you're writing to accomplish the task and the interface is the way that other people use your code.

   * In C, the header file that describes the functions in a library you've written is an interface.

   * In object-oriented programming, the interface to a class is the collection of publicly accessible properties and methods. A good interface contains only public methods. Properties of a class should never be made public but can be exposed through public methods, also called getters and setters.

2. **Deciding on an Exposed Interface**

   * The question of how other programmers will interact with your objects come into play when designing a class.

   * In C++, a class's properties and methods can each be public, protected, or private. 

   * Designing the exposed interface is all about choosing what to make public. 

   * When working on a large project with other programmers, you should view the exposed interface design as a process.

   Consider the Audience

   * The first step in designing an exposed interface is to consider whom you are designing it for. 

   * Is your audience another member of your team? Is this an interface that you will personally be using? Is it something that a programmer external to your company will use? Perhaps a customer? 

   * If the interface is for your own use, you probably have more freedom to iterate on the design. You can change it to suit your own needs. However, you should keep in mind that roles on an engineering team change and it is quite likely that, some day, others will be using this interface as well.

   * Designing an interface for other internal programmers to use is slightly different. In a way, your interface becomes a contract with them. 

   * If the client is an external customer, you will be designing with a very different set of requirements. Ideally, the target customer will be involved in specifying what functionality your interface exposes. You'll need to consider both the specific features they want as well as what customers might want in the future.

   Consider the Purpose

   * There are many reasons for writing an interface. 

   * Before putting any code on paper or even deciding on what functionality you're going to expose, you need to understand the purpose of the interface.

   Application Programming Interface

   * An API is an externally visible mechanism to extend a product or use its functionality within another context.

   * As a common, "A good API makes the easy case easy and the hard case possible". That is, APIs should have a simple learning curve. 

   * The main tradeoff in designing an API is usually ease of use versus flexibility.

   Consider the Future

   * As you are designing your interface, keep in mind what the future holds. 

   * Talk to them and get a better understanding of their use case.

   * Don't design the be-all if the future uses are unclear, because it might unnecessarily complicate the design, the implementation, and its public interface.

3. **Designing a Successful Abstraction**

   * Experience and iteration are essential to good abstractions. 

   * Truly well-designed interfaces come from years of writing and using other abstractions. 

   * You can also leverage someone else's years of writing and using abstractions by reusing existing, well-designed abstractions in the form of standard design patterns.

   * As you encounter other abstractions, try to remember what worked and what didn't work.

   * Don't be afraid to change the abstraction once coding has begun, even if means forcing other programmers to adapt. Hopefully, they'll realize that a good abstraction is benefical to everyone in the long term.

   * Sometimes you need to evangelize a bit when communicating your design to other programmers. Perhaps the rest of the team didn't see a problem with the previous design or feels that your approach requires too much work on their part. In those situations, be prepared both to defend your work and to incorporate their ideas when appropriate.

   * A good abstraction means that the interface has only public methods. All code should be in the implementation file and not in the class definition file. This means that the interface files containing the class definitions are stable and will not change. A specific technique to accomplish this is called private implementation.

   * Iteration is worth mentioning again because it is the most important point. Seek and respond to feedback on your design, change it when necessary, and learn from mistakes.

# CHAPTER 6 Designing for Reuse

What's In This Chapter?

1. The reuse philosophy: Why you should design code for reuse
2. How to design reusable code
 2.1 How to use abstraction
2.2 Strategies for structuring your code for reuse
2.3 Six strategies for designing usable interfaces
2.4 How to reconcile generality with ease of use
3. The SOLID principles

Reusing libraries and other code in your programs is an important design strategy. However, it is only half of the reuse strategy. The other half is designing and writing the code that you can reuse in your program.

> **1. The Reuse Philosophy**

* Write once, use often

* Avoid code duplication at any cost

- DRY - Don't Repeat Yourself

> **2. How To Design Reusable**

- Reusable code fullfills two main goals. 
- First, it is general enough to use for slightly different purposes or in different application domains. Program components with details of a specific application are difficult to reuse in other programs. 
- Second, reusable code is also easy to use. It doesn't require significant time to understand its interface or functionality. Programmers must be able to incorporate it readily into their applications.
- You can deliver it in source form and clients just incorporate your source into their project. Another option is to deliver a static library, or a DLL or shared library. 
- The most important strategy for designing reusable code is abstraction. Chapter 4 presents the real-world analogy of a television, which you can use through its interfaces without understanding how it works inside. Similarly, when you design code, you should clearly separate the interface from the implementation. This separation makes the code easier to use, primarily because clients do not need to understand the internal implementation details in order to use the functionality. 
- Abstraction separates code into interfaces and implementation, so designing reusable code focuses on these two main areas. First, you must structure the code appropriately. What class hierarchies will you use? Should you use templates? How should you divide the code into subsystems?
- Second, you must design interfaces, which are the "entries" into your library, or code that programmers use, to access the functionality you provide.

> **3. Use Abstraction**

- The principle of abstraction, you should provide interfaces to your code that hide the underlying implementation details. There should be a clear distinction between the interface and the implementation. 
- Using abstraction benefits both you and the clients who use your code. 
- Clients benefit because they don't need to worry about the implementation details; they can take advantage of the functionality you offer without understanding how the code really works.
- You benefit because you can modify the underlying code without changing the interface to the code. Thus, you can provide upgrades and fixes without requiring clients to change their use. With dynamically linked libraries, clients might not even need to rebuild their executables.
- Abstraction is so important that it should guide your entire design. As part of every decision you make, ask yourself whether your choice fulfills the principle of abstraction. Put yourself in your client's shoes and determine whether or not you're requiring knowledge of the internal implementation in the interface. 

> **4. Structure Your Code for Optimal Reuse**

- You must consider reuse from the beginning of your design, on all levels, that is, from a single function, over a class, to entire libraries and frameworks. 

1. **Avoid Combining Unrelated or Logically Separate Concepts**

   * When you desing a component, you should keep it focused on a single task or group of tasks. This is also known as the Single Responsibility Principle (SRP). Don't combine unrelated concepts such as random number generator and an XML parser.

   * Even when you are not designing code specifically for reuse, keep this strategy in mind.

   * Entire programs are rarely reused on their own. Instead, pieces or subsystems of the programs are incorporated directly into other applications, or are adapted for slightly different uses. Thus, you should design your programs so that you divide logically separate functionality into distinct components that can be reused in different programs.

2. **Divide Your Programs into Logical Subsystems**

   * You should design your subsystems as discrete components that can be reused independently.

   * For example, if you are designing a networked game, keep the networking and graphical user interface aspects in separate subsystems. That way, you can reuse either component without dragging in the other one.

3. **Use Class Hierarchies to Separate Logical Concepts**
   * In addition to dividing your program into logical subsystems, you should avoid combining unrelated concepts at the class level. For example, suppose you want to write a class for a self-driving car. You decide to start with a basic class for a car and incorporate all the self-driving logic directly into it.

4. **Use Aggregation to Separate Logical Concepts**
   * Aggregation models has-a relationship.

5. **Eliminate User Interface Dependicies**
6. **Use Templates for Generic Data Structures and Algorithms**
7. **Provide Appropriate Checks and Safeguards**

8. **Design for Extensibility** 

   * Open/Closed Principle 

   * Open for extension close for modification

9. **Design Usable Interface**
   * Always think about your interfaces from the perspective of someone using them. Do they make sense? Are they what you would expect?

> **5.  The SOLID Principles**

* **Single Responsibility Principle**: A single component should have a single, well-defined responsibility and should not combine unrelated functionality.

* **Open/Closed Principle**: A class should be open to extension(by deriving from it), but closed for modification.

* **Liskov Substitution**: You should be able to replace an instance of an object with an instance of a subtype of that object. 

* **Interface Segregation Principle**: Keep interfaces clean and simple. It is better to have many smaller, well-defined single-responsibility interfaces than to have broad, general-purpose interfaces.

* **Dependecy Inversion Principle**: Use interfaces to invert dependency relationships. 



