Sure! Let's go through **Object-Oriented Programming (OOP) in C++** in detail.

---

## 🧠 What is OOP?

**Object-Oriented Programming** (OOP) is a programming paradigm based on the concept of “**objects**,” which bundle **data** (attributes) and **functions** (methods) together. It helps in organizing complex software and making it easier to maintain, extend, and reuse.

C++ is a powerful OOP language and supports **four main OOP principles**:

---

## 🔑 Four Pillars of OOP in C++

1. **Encapsulation**
2. **Abstraction**
3. **Inheritance**
4. **Polymorphism**

---

## 1. 🧱 Encapsulation

Encapsulation means **hiding the internal state** of an object and **only exposing what is necessary**.

### 📌 In C++:

Use **access specifiers**:

* `private` – accessible only within the class.
* `protected` – accessible in the class and its subclasses.
* `public` – accessible from outside the class.

### ✅ Example:

```cpp
class BankAccount {
private:
    int balance;

public:
    BankAccount() {
        balance = 0;
    }

    void deposit(int amount) {
        if (amount > 0)
            balance += amount;
    }

    int getBalance() {
        return balance;
    }
};
```

🔒 `balance` is hidden. The only way to interact with it is through public methods.

---

## 2. 🧠 Abstraction

Abstraction means **hiding complex implementation details** and showing only the **essential features** of an object.

### ✅ Example:

```cpp
class Car {
public:
    void start() {
        igniteEngine();
        // Other complex logic
    }

private:
    void igniteEngine() {
        // Implementation hidden
    }
};
```

👀 The user only sees `start()`; they don’t care *how* `igniteEngine()` works.

---

## 3. 🧬 Inheritance

Inheritance is a way to **create a new class from an existing class**.

* Promotes **code reuse**.
* Helps with **hierarchical classification**.

### ✅ Syntax:

```cpp
class Animal {
public:
    void speak() {
        cout << "Some sound\n";
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Woof!\n";
    }
};
```

### 🔓 Access Specifiers in Inheritance:

* `public` inheritance → "is-a" relationship.
* `protected` → inherited members become protected.
* `private` → inherited members become private.

---

## 4. 🌀 Polymorphism

**Polymorphism** means **"many forms"**. In C++, this occurs in two ways:

### a) Compile-Time Polymorphism (Function/Operator Overloading)

```cpp
class Print {
public:
    void show(int x) {
        cout << x << endl;
    }

    void show(string s) {
        cout << s << endl;
    }
};
```

### b) Run-Time Polymorphism (Virtual Functions)

Used for **dynamic dispatch** via base class pointers or references.

```cpp
class Animal {
public:
    virtual void speak() {
        cout << "Animal sound\n";
    }
};

class Dog : public Animal {
public:
    void speak() override {
        cout << "Bark\n";
    }
};

int main() {
    Animal* a = new Dog();
    a->speak();  // Bark
}
```

Without `virtual`, it would call the base class version.

---

## 🔧 Key OOP Features in C++

| Feature                  | Description                              |
| ------------------------ | ---------------------------------------- |
| **Class**                | Blueprint for objects                    |
| **Object**               | Instance of a class                      |
| **Constructor**          | Initializes an object                    |
| **Destructor**           | Cleans up when object is destroyed       |
| **this Pointer**         | Refers to current object                 |
| **Static Members**       | Shared among all instances               |
| **Friend Function**      | Can access private members               |
| **Operator Overloading** | Customize operators like `+`, `==`, etc. |

---

### 📦 Example: Putting It All Together

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() {
        cout << "Drawing shape\n";
    }
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing circle\n";
    }
};

int main() {
    Shape* s = new Circle();
    s->draw();  // Output: Drawing circle
    delete s;
}
```

---

## 📘 Best Practices in OOP with C++

* Use **constructor initialization lists**.
* Prefer **composition over inheritance** when appropriate.
* Mark base class destructors as `virtual` if using inheritance.
* Encapsulate data properly.
* Avoid overusing inheritance; favor clear abstractions.

---

