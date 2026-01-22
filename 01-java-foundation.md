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