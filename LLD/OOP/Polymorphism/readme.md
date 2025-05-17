## 🌀 What is Polymorphism?

**Polymorphism** is a core principle of **Object-Oriented Programming (OOP)**. The term means:

> **"Many forms"** — the same function or object behaves differently based on the context.

---

### 📌 Real-Life Analogy

Think of a **"drive"** command:

* When applied to a **Car**, it accelerates on the road.
* When applied to a **Plane**, it takes off.

The same action (`drive`) has **different behaviors** depending on the object—**this is polymorphism**.

---

## 🧠 Why Use Polymorphism?

* To **write flexible and extensible code**
* To allow **interface consistency**
* To implement **dynamic behavior at runtime**
* To support **code reuse** and **modular design**

---

## 🛠️ Types of Polymorphism in C++

C++ supports two main types:

| Type                  | Timing         | Achieved By                                |
| --------------------- | -------------- | ------------------------------------------ |
| Compile-time (Static) | At compilation | Function Overloading, Operator Overloading |
| Run-time (Dynamic)    | At runtime     | Virtual Functions and Inheritance          |

---

## 🔹 Compile-Time (Static) Polymorphism

### 1. **Function Overloading**

Multiple functions with the **same name** but **different parameters**.

```cpp
class Print {
public:
    void display(int x) {
        cout << "Integer: " << x << endl;
    }

    void display(string s) {
        cout << "String: " << s << endl;
    }
};
```

➡️ Resolved by the **compiler** based on arguments.

---

### 2. **Operator Overloading**

Operators behave differently depending on the types they’re applied to.

```cpp
class Complex {
public:
    int real, imag;

    Complex(int r, int i) : real(r), imag(i) {}

    Complex operator + (const Complex& c) {
        return Complex(real + c.real, imag + c.imag);
    }
};
```

➡️ You can now use `+` with `Complex` objects.

---

## 🔸 Run-Time (Dynamic) Polymorphism

This is achieved using:

* **Inheritance**
* **Virtual Functions**
* **Function Overriding**
* **Base class pointers**

### ✅ Example:

```cpp
class Animal {
public:
    virtual void speak() {
        cout << "Animal speaks\n";
    }
};

class Dog : public Animal {
public:
    void speak() override {
        cout << "Dog barks\n";
    }
};

int main() {
    Animal* a = new Dog();
    a->speak();  // Output: Dog barks
    delete a;
}
```

### 🔍 Key Concepts:

| Term                 | Meaning                                                            |
| -------------------- | ------------------------------------------------------------------ |
| **Virtual Function** | A method in a base class marked with `virtual` to allow overriding |
| **Override**         | Redefines the base class’s method in the derived class             |
| **Base Pointer**     | Can point to objects of base or derived class                      |
| **Dynamic Dispatch** | Actual method call is resolved at runtime                          |

---

## 🧬 Virtual vs Non-Virtual Behavior

```cpp
class A {
public:
    void show() {
        cout << "A show()\n";
    }
};

class B : public A {
public:
    void show() {
        cout << "B show()\n";
    }
};

int main() {
    A* ptr = new B();
    ptr->show();  // Output: A show() ❌ No polymorphism without virtual
}
```

🔁 Add `virtual void show()` in class `A` to fix this.

---

## 🧩 Pure Virtual Functions & Abstract Classes

Used to enforce polymorphism via **interfaces**.

```cpp
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
```

* `Shape` is now an **abstract class**.
* You **cannot instantiate** it directly.
* Forces all derived classes to implement `draw()`.

---

## 🧱 Virtual Table (vtable)

Behind the scenes:

* Each class with virtual functions has a **vtable** (virtual table).
* Object with virtual methods contains a hidden pointer to this table.
* At runtime, the appropriate method is called from the vtable.

This enables **dynamic dispatch**.

---

## ⚠️ Common Pitfalls in Polymorphism

| Mistake                                | Description                                               |
| -------------------------------------- | --------------------------------------------------------- |
| Not using `virtual` in base class      | Prevents polymorphism                                     |
| Forgetting `override` in derived class | Compiles but may not behave as expected                   |
| Not using a `virtual` destructor       | Leads to **memory leaks** when deleting via base pointer  |
| Object slicing                         | Happens when derived objects are copied into base objects |

---

## 🧹 Virtual Destructors

Always declare base class destructors as **virtual** when dealing with polymorphism.

```cpp
class Base {
public:
    virtual ~Base() {
        cout << "Base Destructor\n";
    }
};

class Derived : public Base {
public:
    ~Derived() {
        cout << "Derived Destructor\n";
    }
};
```

Otherwise, only the base destructor gets called when deleting via a base pointer.

---

## 🧠 Summary Table

| Feature          | Description                             |
| ---------------- | --------------------------------------- |
| **Polymorphism** | Same interface, different behavior      |
| **Compile-Time** | Function & Operator Overloading         |
| **Run-Time**     | Inheritance + Virtual Functions         |
| **Tools**        | `virtual`, `override`, base pointers    |
| **Benefits**     | Flexibility, Extensibility, Reusability |

---

## 🧪 Practice Suggestions

1. Create a `Shape` base class with derived classes like `Circle`, `Square`, and implement `draw()`.
2. Use base class pointers to call overridden functions.
3. Explore virtual destructors and object slicing scenarios.

---
