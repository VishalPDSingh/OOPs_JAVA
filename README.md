# Java OOPs Concepts 🚀

This repository contains implementations and examples of **Object-Oriented Programming (OOP)** concepts in Java.  
It is designed for beginners and intermediate learners to understand how Java applies the principles of OOP in real-world programming.

---

## 📖 Topics Covered
- **Class & Object** – Defining and creating objects
- **Constructors** – Default, parameterized, and copy constructors
- **Inheritance** – Single, multilevel, and hierarchical inheritance
- **Polymorphism** – Compile-time (method overloading) and runtime (method overriding)
- **Abstraction** – Using abstract classes and methods
- **Encapsulation** – Data hiding with getters and setters
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

1. **Single Inheritance**  
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


2. **Multiple Inheritance**

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




