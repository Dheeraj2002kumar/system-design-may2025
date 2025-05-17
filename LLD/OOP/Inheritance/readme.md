## 🧬 What is Inheritance?

**Inheritance** is a fundamental concept of **Object-Oriented Programming (OOP)**. It allows a class (called the **derived class** or **child class**) to **inherit** properties and behaviors (data and methods) from another class (called the **base class** or **parent class**).

### 📌 Definition:

> Inheritance enables **code reuse**, establishes a **hierarchical relationship**, and promotes **polymorphism**.

---

## 🧠 Real-Life Analogy

Imagine a **class hierarchy of animals**:

* 🐾 A **generic Animal** can eat and sleep.
* 🐶 A **Dog** is an Animal, but also has behaviors like barking.

Rather than re-writing all code for Dog, we **inherit** from Animal and add Dog-specific features.

---

## 🔧 Syntax in C++

```cpp
class Base {
    // base class members
};

class Derived : access_specifier Base {
    // derived class members
};
```

* `access_specifier` can be `public`, `protected`, or `private` and determines the accessibility of inherited members.

---

## 🧪 Simple Example

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "This animal eats food.\n";
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Dog barks.\n";
    }
};

int main() {
    Dog d;
    d.eat();   // Inherited from Animal
    d.bark();  // Defined in Dog
    return 0;
}
```

✔️ `Dog` class **inherits** `eat()` from `Animal`.

---

## 🔓 Types of Inheritance in C++

C++ supports **5 types of inheritance**:

### 1. **Single Inheritance**

* One base → One derived.

```cpp
class A { };
class B : public A { };
```

### 2. **Multiple Inheritance**

* Derived class inherits from **more than one base class**.

```cpp
class A { };
class B { };
class C : public A, public B { };
```

🧨 **Note:** May cause ambiguity (e.g., diamond problem).

### 3. **Multilevel Inheritance**

* Class inherits from a derived class.

```cpp
class A { };
class B : public A { };
class C : public B { };
```

### 4. **Hierarchical Inheritance**

* Multiple classes inherit from a single base class.

```cpp
class A { };
class B : public A { };
class C : public A { };
```

### 5. **Hybrid Inheritance**

* A combination of two or more types.

```cpp
class A { };
class B : public A { };
class C { };
class D : public B, public C { };
```

---

## 🔒 Access Specifiers in Inheritance

| Inherited Members | `public` Inheritance | `protected` Inheritance | `private` Inheritance |
| ----------------- | -------------------- | ----------------------- | --------------------- |
| `public`          | public               | protected               | private               |
| `protected`       | protected            | protected               | private               |
| `private`         | Not inherited        | Not inherited           | Not inherited         |

✅ **Common usage**: Use `public` inheritance for **“is-a” relationships**.

---

## 🧩 Virtual Inheritance (Diamond Problem)

### 🧠 Problem:

In **multiple inheritance**, if two base classes inherit from the same base, and a derived class inherits from both, ambiguity occurs.

```cpp
class A {
public:
    void show() { cout << "A"; }
};

class B : public A { };
class C : public A { };
class D : public B, public C { };

int main() {
    D obj;
    // obj.show(); ❌ Ambiguous
}
```

### ✅ Solution: Use **virtual inheritance**

```cpp
class A {
public:
    void show() { cout << "A"; }
};

class B : virtual public A { };
class C : virtual public A { };
class D : public B, public C { };

int main() {
    D obj;
    obj.show();  // ✅ No ambiguity
}
```

---

## 🎯 Use-Cases of Inheritance

* Modeling real-world relationships (`Car` is a `Vehicle`)
* Code reusability
* Frameworks & libraries (e.g., GUI frameworks)
* Implementing **polymorphism** (e.g., overriding `draw()` in different shapes)

---

## 🔃 Method Overriding

In derived classes, you can override base class methods:

```cpp
class Base {
public:
    virtual void greet() {
        cout << "Hello from Base\n";
    }
};

class Derived : public Base {
public:
    void greet() override {
        cout << "Hello from Derived\n";
    }
};
```

✔️ Use `virtual` keyword in the base class and `override` in the derived class for clarity and safety.

---

## 🚫 When Not to Use Inheritance

* Don't use inheritance **just for code reuse**—prefer **composition** if the relationship isn't truly "is-a".
* Don’t inherit from concrete classes unnecessarily—use **abstract classes** or **interfaces** for flexibility.

---

## 🧠 Summary Table

| Feature               | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| **Inheritance**       | Acquiring properties and methods of a base class in a derived class   |
| **Base Class**        | The class being inherited from                                        |
| **Derived Class**     | The class that inherits                                               |
| **Access Specifiers** | Controls how members are inherited (`public`, `protected`, `private`) |
| **Virtual Functions** | Enable dynamic (runtime) polymorphism                                 |
| **Types**             | Single, Multiple, Multilevel, Hierarchical, Hybrid                    |

---

## 🛠️ Practice Ideas

1. Model a `Vehicle` → `Car`, `Truck`, `Bike` hierarchy.
2. Create a `Shape` abstract class and implement `draw()` in `Circle`, `Rectangle`.
3. Try solving the **diamond problem** with and without virtual inheritance.

---
