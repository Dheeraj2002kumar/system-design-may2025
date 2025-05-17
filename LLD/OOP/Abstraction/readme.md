## 🎯 What is Abstraction?

**Abstraction** is an Object-Oriented Programming (OOP) principle that means:

> **Hiding internal implementation details and showing only the necessary features to the user.**

It focuses on **what an object does**, rather than **how it does it**.

---

## 🧠 Key Concept of Abstraction

Imagine you’re using a **TV remote**:

* You press buttons to change channels, adjust volume, or turn it on/off.
* You don’t need to know the electronic circuits inside or how the signal is processed.

That’s **abstraction**—you interact with a simple interface and ignore the complexity underneath.

---

## 🔧 Abstraction in C++

In C++, abstraction is achieved using:

1. **Classes and Objects**
2. **Access Specifiers (public/private)**
3. **Abstract Classes and Pure Virtual Functions**

---

## 1. 📦 Abstraction with Classes and Access Specifiers

Using `private` members, you **hide** internal data. Using `public` methods, you **expose only essential functionality**.

### ✅ Example:

```cpp
#include <iostream>
using namespace std;

class Car {
private:
    void checkEngine() {
        cout << "Checking engine status...\n";
    }

public:
    void start() {
        checkEngine();  // Hidden from user
        cout << "Car started.\n";
    }
};

int main() {
    Car c;
    c.start();  // Simple interface to a complex process
    return 0;
}
```

**What’s happening?**

* User calls `start()`.
* The engine check is abstracted—user doesn't need to see it.

---

## 2. 🧬 Abstraction Using Abstract Classes & Pure Virtual Functions

A **pure virtual function** is a function with no implementation in the base class. A class that contains at least one pure virtual function is called an **abstract class**.

It defines an interface, and the **derived classes must implement it**.

### ✅ Syntax:

```cpp
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
};
```

### ✅ Example:

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() = 0;  // Pure virtual
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle\n";
    }
};

class Rectangle : public Shape {
public:
    void draw() override {
        cout << "Drawing Rectangle\n";
    }
};

int main() {
    Shape* s1 = new Circle();
    Shape* s2 = new Rectangle();
    
    s1->draw();  // Output: Drawing Circle
    s2->draw();  // Output: Drawing Rectangle

    delete s1;
    delete s2;
    return 0;
}
```

**What's happening?**

* `Shape` is an **abstract class**.
* It provides an interface (`draw()`).
* Specific shapes implement their own version of the function.

This is a **perfect example of abstraction**: the client code doesn’t need to know how drawing is implemented—it just calls `draw()`.

---

## 🧱 Difference Between Encapsulation and Abstraction

| Feature           | Encapsulation                          | Abstraction                               |
| ----------------- | -------------------------------------- | ----------------------------------------- |
| Definition        | Hides **data** using access specifiers | Hides **implementation details**          |
| Purpose           | Protect internal state                 | Show only essential features              |
| Achieved via      | Classes, `private/public` members      | Abstract classes, pure virtual functions  |
| Real-life Example | Medicine capsule (wraps content)       | ATMs (only show interface, not mechanics) |

---

## 💡 Benefits of Abstraction

* ✅ **Simplifies complex systems** by hiding unnecessary details
* ✅ **Improves code readability and usability**
* ✅ **Enables modular design**
* ✅ **Reduces coupling** between components
* ✅ **Enhances maintainability** and scalability

---

## 🧪 Real-World Example: Payment System

```cpp
class Payment {
public:
    virtual void pay(float amount) = 0;
};

class CreditCard : public Payment {
public:
    void pay(float amount) override {
        cout << "Paid $" << amount << " using Credit Card.\n";
    }
};

class PayPal : public Payment {
public:
    void pay(float amount) override {
        cout << "Paid $" << amount << " using PayPal.\n";
    }
};

void checkout(Payment* p) {
    p->pay(99.99);
}
```

Here, `checkout()` works with the abstract type `Payment`, and doesn’t care if the user pays with a credit card or PayPal.

---

## 🔍 Summary

| Feature         | Description                                               |
| --------------- | --------------------------------------------------------- |
| **Abstraction** | Hides internal implementation, exposes only the interface |
| **Main Tool**   | Abstract classes and pure virtual functions               |
| **Goal**        | Reduce complexity, increase reusability                   |
| **Example**     | `Shape` class with `draw()` pure virtual function         |

---

## 🚀 What You Should Practice

1. Implement an abstract class `Device` with pure virtual functions `start()` and `shutdown()`, and create classes like `Laptop`, `Phone`.
2. Build a polymorphic payment system using abstract classes.
3. Understand when to use **interface abstraction** versus **simple class-based abstraction**.

---
