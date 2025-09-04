# Java OOPs Concepts 🚀

This repository contains implementations and examples of **Object-Oriented Programming (OOP)** concepts in Java.  
It is designed for beginners and intermediate learners to understand how Java applies the principles of OOP in real-world programming.

---

## 📖 Topics Covered
- **Class & Object** – Defining and creating objects
- **Constructors** – Default, parameterized, and copy constructors
- **Encapsulation** – Data hiding with getters and setters
- **Inheritance** – Single, multilevel, and hierarchical inheritance
- **Polymorphism** – Compile-time (method overloading) and runtime (method overriding)
- **Abstraction** – Using abstract classes and methods
- **Interfaces** – Multiple inheritance using interfaces
- **Access Modifiers** – Public, private, protected, and default
- **Static & Final Keywords** – Usage with variables, methods, and classes




# 📝 Inheritance

Inheritance is a fundamental concept in **OOPs**.  
It is a mechanism in Java by which one class is allowed to inherit the features of another class.

- A class that inherits from another class can reuse the methods and fields of that class.
- Inheritance means creating a new class based on an existing class.

---

### 👨‍👩‍👦 SuperClass
The class whose features are inherited is known as a **SuperClass** (or Parent class).

### 👶 SubClass
The class that inherits from another class is known as a **SubClass** (or Child class).  
- The subclass can add its own fields and methods in addition to the superclass fields and methods.

---

### 🔑 `extends` Keyword
The `extends` keyword is used to inherit properties and behaviors from a superclass.

---

## 📖 Key Points

1. ** ✅ Single Inheritance**  
   - Single inheritance is a type of inheritance where a subclass inherits from only one superclass.  
   - Example:
     ```java
     class Animal {
         void eat() {
             System.out.println("Eating...");
         }
     }

     class Dog extends Animal {
         void bark() {
             System.out.println("Barking...");
         }
     }

     public class TestInheritance {
         public static void main(String[] args) {
             Dog d = new Dog();
             d.eat();   // Inherited method
             d.bark();  // Subclass method
         }
     }
     ```
## 🗒️ Notes

In Java, **private members** (variables or methods) belong only to the class where they are declared.  
Even if a subclass extends that class, it does **not** get direct access to those private members.

---

### ❓ Why?

1. **Encapsulation**  
   - Java follows the principle of **data hiding**.  
   - Private members are meant to be hidden from outside classes — even subclasses — to protect the internal implementation.

2. **Security & Integrity**  
   - Preventing subclasses from accessing or modifying sensitive data ensures controlled access.  
   - Access can be safely provided through **public** or **protected** getters and setters.


2. ** ❌ Multiple Inheritance**

Multiple inheritance is **not permitted in Java** as it leads to the **Diamond Problem**, which results in ambiguity.

🔴 **Problem:**  
Ambiguity in Java occurs in multiple inheritance when **two parent classes have the same method**.  
If a child class tries to inherit from both, the compiler cannot decide which method to use.  
This situation is called the **Diamond Problem**, and that’s why Java does not support multiple inheritance with classes.

---

### 🚫 Example (Not Allowed in Java)
```java
class A {
    void show() {
        System.out.println("Class A method");
    }
}

class B {
    void show() {
        System.out.println("Class B method");
    }
}

// ❌ This will cause compile-time error
class C extends A, B {
    public static void main(String[] args) {
        C obj = new C();
        obj.show();  // Ambiguity: Which show()? A's or B's?
    }
}
```
3. **Multi-level Inheritance**

✅ Multi-level inheritance is **permitted in Java**.  
When multiple classes are involved in a parent-child relationship **in a chain**, it is known as **multi-level inheritance**.

---

### 📖 Example

```java
class GrandParent {
    void displayGrandParent() {
        System.out.println("I am the GrandParent");
    }
}

class Parent extends GrandParent {
    void displayParent() {
        System.out.println("I am the Parent");
    }
}

class Child extends Parent {
    void displayChild() {
        System.out.println("I am the Child");
    }
}

public class TestInheritance {
    public static void main(String[] args) {
        Child c = new Child();

        // Methods from all three levels are accessible
        c.displayGrandParent(); // Inherited from GrandParent
        c.displayParent();      // Inherited from Parent
        c.displayChild();       // Defined in Child
    }
}
```

4. **Cyclic Inheritance**

🚫 **Cyclic inheritance is not permitted in Java.**  
This occurs when a class is trying to inherit itself directly or indirectly, which creates an infinite loop in the inheritance chain.

---

### ❌ Example (Invalid in Java)
```java
// Direct cyclic inheritance
class A extends A {   // Error: cyclic inheritance involving A
}

// Indirect cyclic inheritance
class A extends B { }
class B extends A { }  // Error: cyclic inheritance involving A and B
```

5. **Constructors Do Not Participate in Inheritance**

In Java, **constructors are not inherited**.  
However, when creating a child class object, the **parent constructor is always executed first**. This process is called **constructor chaining**.

---

### 🔗 Constructor Chaining
- Java automatically calls the parent class constructor **before** running the child class constructor.  
- This is done using the special keyword `super()`.  
- If you don’t explicitly write `super()`, the compiler adds it as the **first line** of the child class constructor.  
- `super()` always calls the **zero-argument (default) constructor** of the parent class.  
- If the parent doesn’t have a default constructor, you must explicitly call a parameterized one using `super(arguments)`.

---

### ❓ Why Parent Constructor Is Called?
Because the child object contains the **parent’s state/fields** as well.  
The parent constructor ensures the parent part of the object is **properly initialized** before the child’s constructor executes.

---

### 📌 Important Rules
1. Constructors are **not inherited**.  
2. The first line of every child constructor is **implicitly `super()`** if nothing is written.  
3. `super()` calls the **zero-argument constructor** of the parent.  
4. If no zero-argument constructor exists in the parent, you must call another one explicitly with `super(arguments)`.  

## 🏗️ Default Constructor in Inheritance

- If no constructor is explicitly defined, Java automatically provides a **default (no-argument) constructor**.  
- In inheritance, the **superclass constructor is always called first**.  
- If the parent has no default constructor, the subclass must explicitly call a parameterized one using `super(arguments)`.  

---

### 📖 Example: Default Constructor Chaining

```java
class Parent {
    Parent() {
        System.out.println("Parent class constructor");
    }
}

class Child extends Parent {
    Child() {
        // super();  // automatically inserted by compiler
        System.out.println("Child class constructor");
    }
}

public class Test {
    public static void main(String[] args) {
        Child c = new Child();
    }
}
```
## 🔑 Using `super()` to Call Parent Constructor

- `super()` must be the **first statement** inside a child class constructor.  
- If `super()` is not written, the compiler inserts it automatically.  
- If the parent does not have a **no-argument constructor**, you must explicitly call the correct constructor using `super(arguments)`.  

---

### 📖 Example: Calling Parameterized Parent Constructor

```java
class Parent {
    Parent(String msg) {
        System.out.println("Parent says: " + msg);
    }
}

class Child extends Parent {
    Child() {
        super("Hello from Child!"); // must call explicitly
        System.out.println("Child class constructor");
    }
}

public class Test {
    public static void main(String[] args) {
        Child c = new Child();
    }
}
```
## 🌳 The Object Class in Java

- In Java, every class **implicitly inherits** from `java.lang.Object`, unless it explicitly extends another class.  
- It is the **root class** of the Java class hierarchy.  
- The `Object` class provides several useful common methods that are available to all classes:

### 🔑 Common Methods of Object Class
1. `toString()` → Returns a string representation of the object.  
2. `equals(Object obj)` → Compares two objects for equality.  
3. `hashCode()` → Returns an integer hash code value for the object.  
4. `getClass()` → Returns the runtime class of the object.  
5. `clone()` → Creates and returns a copy of the object.  

---

### 📖 Example: Using Object Class Methods

```java
class MyClass {
    int id;
    String name;

    MyClass(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

public class TestObject {
    public static void main(String[] args) {
        MyClass obj = new MyClass(1, "Singh");

        // Object class methods
        System.out.println("toString(): " + obj.toString());
        System.out.println("hashCode(): " + obj.hashCode());
        System.out.println("getClass(): " + obj.getClass());

        // Comparing objects
        MyClass obj2 = new MyClass(1, "Singh");
        System.out.println("equals(): " + obj.equals(obj2));
    }
}
```

## 🏗️ Parameterized Constructor in Inheritance

- `super(parameters)` calls the **parameterized constructor** of the parent class.  
- This is part of **constructor chaining**, where the subclass constructor explicitly invokes its superclass constructor.  
- The **first line** of a constructor can only be either `super()` or `this()`.  
- When a subclass variable **shadows** a parent variable, `super` can be used to refer to the **parent’s version**.

---

### 📖 Example 1: Calling Parameterized Parent Constructor

```java
class Parent {
    String name;

    Parent(String name) {
        this.name = name;
        System.out.println("Parent constructor called: " + name);
    }
}

class Child extends Parent {
    int age;

    Child(String name, int age) {
        super(name); // calls Parent(String name)
        this.age = age;
        System.out.println("Child constructor called: " + name + ", Age: " + age);
    }
}

public class Test {
    public static void main(String[] args) {
        Child c = new Child("Singh", 21);
    }
}
```
## 🔎 Difference: `super()` vs `super` in Java

Although they look similar, `super()` and `super` are used for **different purposes** in inheritance.

---

### 1️⃣ `super()`
- Calls the **constructor of the parent class** (default or parameterized).  
- Must be the **first statement** in the child constructor.  
- Used in **constructor chaining**.

📖 **Example: Using `super()`**
```java
class Parent {
    Parent() {
        System.out.println("Parent default constructor");
    }

    Parent(String msg) {
        System.out.println("Parent says: " + msg);
    }
}

class Child extends Parent {
    Child() {
        super("Hello from Child"); // calls Parent(String msg)
        System.out.println("Child constructor");
    }
}

public class TestSuperConstructor {
    public static void main(String[] args) {
        Child c = new Child();
    }
}
```

**2️⃣ super**

- Refers to the **immediate parent class object**.  
- Used to access:  
  - Parent **variables** (when child shadows them).  
  - Parent **methods** (when child overrides them).  

---

### 📖 Example: Using `super`

```java
class Parent {
    String role = "Parent Role";

    void display() {
        System.out.println("Method in Parent");
    }
}

class Child extends Parent {
    String role = "Child Role";

    void display() {
        System.out.println("Method in Child");
        super.display();  // call parent's method
    }

    void showRoles() {
        System.out.println("Child role: " + role);
        System.out.println("Parent role: " + super.role);
    }
}

public class TestSuperKeyword {
    public static void main(String[] args) {
        Child c = new Child();
        c.display();
        c.showRoles();
    }
}
```

## 🔗 Using `super` in Multi-Level Inheritance

In a multi-level inheritance chain, `super` can be used at each level to:
- Call the **immediate parent’s method** (even if overridden).
- Access the **parent’s variable** when shadowed.

---

### 📖 Example: Multi-Level Inheritance with `super`

```java
class GrandParent {
    String role = "GrandParent Role";

    void display() {
        System.out.println("Method in GrandParent");
    }
}

class Parent extends GrandParent {
    String role = "Parent Role";

    @Override
    void display() {
        System.out.println("Method in Parent");
        super.display(); // calls GrandParent method
    }
}

class Child extends Parent {
    String role = "Child Role";

    @Override
    void display() {
        System.out.println("Method in Child");
        super.display(); // calls Parent's display()
    }

    void showRoles() {
        System.out.println("Child role: " + role);
        System.out.println("Parent role: " + super.role); // access Parent's variable
    }
}

public class TestSuperMultiLevel {
    public static void main(String[] args) {
        Child c = new Child();
        c.display();
        c.showRoles();
    }
}
```
6. **Hierarchical Inheritance**

✅ Hierarchical inheritance is **permitted in Java**.  
It occurs when **multiple subclasses inherit from a single superclass**.  

---

### 📖 Example: Hierarchical Inheritance

```java
class Animal {
    void eat() {
        System.out.println("This animal eats food");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {
    void meow() {
        System.out.println("Cat meows");
    }
}

public class TestHierarchical {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();   // inherited from Animal
        d.bark();  // Dog specific

        Cat c = new Cat();
        c.eat();   // inherited from Animal
        c.meow();  // Cat specific
    }
}
```