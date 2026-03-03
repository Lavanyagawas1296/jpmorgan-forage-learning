01️⃣ Java: Class & Object
What confused me

I mixed up class and object and couldn’t visualize what actually exists in memory.

What I understood

Class = blueprint

Object = real instance created from the blueprint

Example
class Car {
    int speed;
}

Car c1 = new Car();


Car → class

c1 → object

Key takeaway

Objects are created using new.
Each object has its own copy of non-static variables.

02️⃣ Constructors
What confused me

Why constructors exist and when they are called.

What I understood

A constructor runs automatically when an object is created

It is used to initialize the object

Example
class Car {
    int speed;

    Car() {
        speed = 0;
    }
}

Car c1 = new Car(); // constructor runs ONCE

Key rule

Constructor runs once per object creation.

03️⃣ Static Keyword (VERY IMPORTANT)
What confused me

Difference between static variable and normal variable, and access rules.

What I understood

static → belongs to the class

non-static → belongs to the object

Example
class Test {
    static int x = 10;
    int y = 5;
}

Test t1 = new Test();
Test t2 = new Test();


x → 1 copy

y → 2 copies

Access rules

Static method ❌ cannot directly access non-static variable

Non-static method ✅ can access static variable

Why main is static

Because Java needs to start the program without creating an object first.

04️⃣ Packages & Imports
What confused me

Why packages exist and when to use import.

What I understood

Package = folder

Used to organize code and avoid name conflicts

Example
package com.bank.app.service;


Folder structure must be:

com/bank/app/service/ClassName.java

Import rule

Same package → ❌ no import needed

Different package → ✅ import required

import com.bank.app.entity.User;

Why packages matter

Clean structure

Easy debugging

Easy teamwork

05️⃣ OOP Principles (Core Concept)
What confused me

Difference between abstraction and encapsulation

Why inheritance is needed

Real use of polymorphism

What I understood

Java follows 4 main OOP principles:

1. Encapsulation

Hiding data using private variables and exposing through getters/setters.

class User {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

Why?
To protect data from direct modification.

2. Abstraction

Hiding implementation details.

abstract class Animal {
    abstract void sound();
}

User only knows what it does, not how it works.

3. Inheritance

Reusing parent class properties.

class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
}

Dog automatically gets eat() method.

4. Polymorphism

Same method, different behavior.

class Animal {
    void sound() {
        System.out.println("Some sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Bark");
    }
}

Method overriding = runtime polymorphism.

Key takeaway

OOP makes code:

Reusable

Maintainable

Scalable

06️⃣ Interfaces vs Abstract Class
What confused me

When to use interface?

Why both exist?

What I understood
Interface

100% abstraction (mostly)

Multiple inheritance allowed

interface Payment {
    void pay();
}
Abstract Class

Can have abstract + normal methods

Only single inheritance

abstract class Shape {
    abstract void draw();

    void display() {
        System.out.println("Shape");
    }
}
Difference Summary
Feature	Interface	Abstract Class
Multiple inheritance	✅	❌
Constructors	❌	✅
Variables	public static final	Any type
Use case	Contract	Base class
07️⃣ Exception Handling
What confused me

Checked vs Unchecked exceptions

Why try-catch is needed

What I understood

Exceptions prevent program crash.

Syntax
try {
    int a = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Error occurred");
}
Types

Checked → Compile-time (IOException)
Unchecked → Runtime (NullPointerException)

Finally block
finally {
    System.out.println("Always runs");
}

Runs whether exception happens or not.

Key takeaway

Proper exception handling = stable backend.

08️⃣ Collections Framework
What confused me

Difference between List, Set, Map

When to use which

What I understood
List

Ordered

Allows duplicates

List<String> list = new ArrayList<>();
Set

No duplicates

Set<String> set = new HashSet<>();
Map

Key-value pair

Map<Integer, String> map = new HashMap<>();
When to use what?
Situation -> Use
Ordered data ->	List
Unique values -> Set
Key-value lookup -> Map
