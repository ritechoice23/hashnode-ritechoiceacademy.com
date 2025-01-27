---
title: "Learn OOP in PHP without the noise"
seoTitle: "Master OOP in PHP Easily"
seoDescription: "Master PHP OOP: Learn classes, encapsulation, inheritance, polymorphism, interfaces, and abstract classes with real-world examples"
datePublished: Mon Jan 27 2025 09:35:53 GMT+0000 (Coordinated Universal Time)
cuid: cm6euslgj000d0al4fg21eosz
slug: learn-oop-in-php-without-the-noise
tags: oop, php, phpstorm, php8, oop-in-php

---

Without the noise, using simple, real-world examples, I'll teach you Object-Oriented Programming (OOP) in PHP in this post. Let's break this down step by step.

### **Classes and Objects**

Think of a class as a blueprint, and objects as things created from that blueprint.

```php
// This is our blueprint (class)
class Car {
    // Properties (characteristics)
    public $brand;
    public $color;

    // Method (action)
    public function startEngine() {
        return "Vroom! The $this->color $this->brand is starting.";
    }
}

// Creating objects from the blueprint
$myCar = new Car();
$myCar->brand = "Toyota";
$myCar->color = "Red";
echo $myCar->startEngine(); // Outputs: Vroom! The Red Toyota is starting.

```

### **Constructor**

This is like a setup method that runs when you create a new object:

```php
class Dog {
    public $name;
    public $breed;

    // Constructor
    public function __construct($name, $breed) {
        $this->name = $name;
        $this->breed = $breed;
    }
}

$myDog = new Dog("Buddy", "Golden Retriever");

```

### **Encapsulation**

This means protecting your data by making it private and providing public methods to access it:

```php
class BankAccount {
    private $balance = 0; // Can't access directly from outside

    public function deposit($amount) {
        if ($amount > 0) {
            $this->balance += $amount;
            return "Deposited $" . $amount;
        }
    }

    public function getBalance() {
        return $this->balance;
    }
}

```

### **Inheritance**

This allows a class to inherit properties and methods from another class:

```php
class Animal {
    public function eat() {
        return "I'm eating!";
    }
}

class Cat extends Animal {
    public function meow() {
        return "Meow!";
    }
}

$myCat = new Cat();
echo $myCat->eat();  // From parent class: "I'm eating!"
echo $myCat->meow(); // From child class: "Meow!"

```

### **Polymorphism**

This means different classes can have methods with the same name that work differently:

```php
class Bird {
    public function makeSound() {
        return "Tweet tweet!";
    }
}

class Duck extends Bird {
    public function makeSound() {  // Same method name, different behavior
        return "Quack quack!";
    }
}

```

### **Interfaces**

These are like contracts that classes must follow:

```php
interface Vehicle {
    public function accelerate();
    public function brake();
}

class Bicycle implements Vehicle {
    public function accelerate() {
        return "Pedaling faster!";
    }

    public function brake() {
        return "Squeezing brakes!";
    }
}

```

### **Abstract Classes**

These are partial blueprints that other classes must complete:

```php
abstract class Shape {
    abstract public function calculateArea();
}

class Circle extends Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function calculateArea() {
        return pi() * $this->radius * $this->radius;
    }
}

```

These are the fundamental concepts of OOP in PHP, if you have any questions feel free to ask in the comment.