# OOPS-Interview-Questions

Here is a detailed explanation of the 50 most common OOP interview questions in C++, with expanded answers and illustrative code snippets to help you deeply understand and articulate OOP concepts:

1. What is Object-Oriented Programming (OOP) in C++?
 
Object-Oriented Programming is a paradigm that models software as a collection of cooperating objects rather than functions and logic. In C++, OOP allows you to group both data and functions that operate on that data into a single unit, called a class. This approach enables four main principles: encapsulation, inheritance, abstraction, and polymorphism.

2. What are the main principles of OOP?

Encapsulation: Data and methods are bundled together; data is hidden from outside interference.

Abstraction: Complexity is hidden by exposing only essential features.

Inheritance: Allows new classes to use properties and methods of existing ones.

Polymorphism: Same function name behaves differently on different classes.

3. What’s the difference between a class and an object?
   
A class is a user-defined template for creating objects, containing attributes and methods.
An object is an instance of a class.

cpp
class Car { // class
  public:
    void drive() { }
};
Car myCar; // object

4. What is encapsulation? Give an example in C++.

Encapsulation is the technique of hiding the internal state of an object and requiring all interaction to be performed through an object’s methods.

cpp
class Account {
  private:
    double balance;
  public:
    void deposit(double amt) { balance += amt; }
    double getBalance() { return balance; }
};
Here, "balance" can’t be accessed directly outside the class.


5. Describe abstraction in C++.

Abstraction is the process of showing only essential details while hiding the background details. In C++, abstraction is implemented using abstract classes and interfaces (pure virtual functions):

cpp
class Shape {
  public:
    virtual void draw() = 0; // pure virtual function
};

6. What is inheritance? Types in C++?

Inheritance lets a class acquire properties and behaviors from another class. C++ supports:

Single (one base, one derived)

Multiple (one derived, multiple bases)

Multilevel (derived from derived)

Hierarchical (one base, multiple derived)

Hybrid (combination)

cpp
class Animal { };
class Dog : public Animal { }; // Single inheritance

7. What is polymorphism? Explain its types.

Polymorphism means “many forms.” C++ supports:

Compile-time (static): via function or operator overloading.

Run-time (dynamic): via virtual functions.

cpp
// Compile-time
void print(int i);
void print(double f);

// Run-time
class Base {
  public: virtual void show() { cout << "Base"; }
};
class Derived : public Base {
  public: void show() override { cout << "Derived"; }
};


8. What are access specifiers?

Access specifiers control visibility/scoping:

private: accessible only within the class.

protected: accessible in the class and its derived classes.

public: accessible everywhere.


9. Explain function overloading and overriding.
   
Overloading: Functions with the same name but different parameter lists within the same scope.

Overriding: Redefining a base class’s virtual function in a derived class with the same signature.


10. What is a constructor? Types?

A constructor is a special function called when an object is created.

Default constructor: No params.

Parameterized constructor: One or more params.

Copy constructor: Initializes from another object.

cpp
class Demo {
  public:
    Demo() { } // default
    Demo(int a) { } // parameterized
    Demo(const Demo &d) { } // copy
};


11. What is a destructor?

A destructor is a special function called when an object goes out of scope. Used for cleanup. In C++, it’s defined as ~ClassName().


12. What is the difference between struct and class?
 
In a struct, members are public by default; in a class, they are private. Apart from this, both can have functions and support most features.


14. What is a virtual function?
 
It’s a function in a base class declared with the virtual keyword, meant to be overridden in derived classes. Enables dynamic dispatch.


15. What is a pure virtual function and abstract class?
A function with = 0:

cpp
virtual void display() = 0;
A class with at least one pure virtual function is abstract and can’t be instantiated.


15. Can a constructor be virtual in C++?
No. Constructors cannot be virtual since they are not inherited.


16. What is multiple inheritance? Does C++ support it?
A class can inherit from more than one class. Yes, C++ supports it.

cpp
class A { };
class B { };
class C : public A, public B { };


17. What is the diamond problem?
In multiple inheritance, if two base classes inherit from the same grandparent, and a derived inherits from both, ambiguity (the diamond problem) can arise. Solution: virtual inheritance.



18. What is operator overloading? Example?
Redefines the meaning of an operator for user-defined types.

cpp
Complex operator+(const Complex& c);
// enables c1 + c2 if both are Complex


19. Explain friend functions.
A friend function can access private and protected members of a class but isn't a member itself:

cpp
class Box {
  friend void printBox(Box b);
};


20. What are static members and static member functions?
Static members: Shared across all objects.
Static functions: Only use static data and can be called without objects.

cpp
class Counter {
  static int count;
  static void increment() { count++; }
};


21. What is the ‘this’ pointer?
It’s a pointer to the calling object, used to refer to object members.

cpp
void setValue(int v) { this->val = v; }


22. What is tight coupling vs. loose coupling?
Tight coupling: Classes are highly dependent (fragile).
Loose coupling: Classes interact via interfaces, making code easier to change and test.


23. How does C++ implement data hiding?
Using private/protected access specifiers, restricting external access to data.


24. What are the benefits of OOP?
Code reusability

Maintainability

Security

Modularity

Extensibility

25. Difference between compile-time and run-time polymorphism?
Compile-time: Achieved using function or operator overloading.

Run-time: Achieved using virtual functions.


26. What is object slicing?
When a derived object is assigned to a base class variable, the derived-specific attributes are “sliced off.” Only the base part remains.



27. What is an inline function?
A function prefixed with inline so its code replaces the call site, reducing function call overhead (best for small functions).



28. Can we provide implementation of a function inside a class?
Yes, and those functions are implicitly inline.

cpp
class Test {
  void show() { cout << "Hello"; } // inline by default
};


29. What is upcasting and downcasting?
Upcasting: Using a base class pointer to refer to a derived class object.

Downcasting: Casting a base pointer to a derived pointer; requires dynamic_cast.

cpp
Base* b = new Derived();
Derived* d = dynamic_cast<Derived*>(b);
30. What is the use of the virtual destructor?
Ensures the derived class’s destructor is invoked when deleting via a base pointer, avoiding resource leaks.

cpp
class Base {
  public:
    virtual ~Base() { }
};


31. What is dynamic binding?
Function to execute is decided at runtime using virtual functions.


32. What is static binding?
Function to execute is resolved at compile-time, for non-virtual functions.


33. What is an interface?
C++ does not have interfaces like Java. Abstract classes with only pure virtual functions act as interfaces.


34. What is encapsulation vs. abstraction difference?
Encapsulation: Bundles data with methods; restricts access.

Abstraction: Shows only essential details, hiding complexity.


35. What are default and delete keywords in C++11?
default: Forces the compiler to generate a default implementation (e.g., constructor).

delete: Prevents the compiler from generating a function, such as a copy constructor.

cpp
class X {
  X() = default;
  X(const X&) = delete;
};


36. What are smart pointers? Types?
Smart pointers are class templates that handle memory automatically. Types:

unique_ptr: Single owner.

shared_ptr: Shared ownership.

weak_ptr: Non-owning, prevents cyclical references.


37. Explain RAII (Resource Acquisition Is Initialization).
C++ idiom binding resource lifecycle to object lifetime; ties allocation to construction and deallocation to destruction, preventing leaks.



38. What is the role of access specifiers in inheritance?
They affect visibility of base class members in derived classes via types of inheritance:

public: keeps access levels as is.

protected: all public and protected members become protected.

private: all public and protected become private.



39. What is late binding?
Another term for dynamic binding; actual function call is determined at runtime.


40. Explain the Copy Constructor.
A constructor used to create a new object as a copy of an existing object.

cpp
class Demo {
  public:
    Demo(const Demo& d) { }
};


41. What is the use of explicit keyword?
Prevents the compiler from using a constructor for implicit conversions.

cpp
explicit MyClass(int x);


42. How do templates relate to OOP in C++?
Templates allow generic programming, enabling classes and functions to work with any type.

cpp
template <class T>
class Stack { };


43. What are manipulators in C++?
Functions that change formatting of output/input streams (e.g., std::setw, std::endl).


44. What operators cannot be overloaded in C++?
You cannot overload :: (scope resolution), . (member access), .*, ?:, sizeof, or typeid.


45. What is casting? Types?
Casting converts types. In C++:

static_cast

dynamic_cast

const_cast

reinterpret_cast


46. What is the significance of the scope resolution operator (::)?

It accesses global variables, static class members, and defines functions outside class:

cpp
int value;
void MyClass::func() { ... }


47. What is a namespace? How is it related to OOP?

A namespace is a logical grouping to avoid name conflicts, especially in large OOP projects.

cpp
namespace myspace {
  class Demo { };
}


48. What is method hiding?

If a derived class function has the same name as base but isn’t declared virtual, the base function is hidden—not overridden.


49. Explain hierarchy of exception classes in C++.

Rooted at std::exception, which is the base class. Other standard exceptions derive from it (e.g., std::runtime_error), enabling OOP error handling.


50. Should destructors be virtual in base classes?

Yes, to ensure proper resource cleanup in polymorphic class hierarchies when deleting derived objects via base pointers.
