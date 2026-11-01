# Abstraction

Abstraction focuses on **what an object can do** while hiding details about **how it does it**. It helps callers use a small, stable set of operations without depending on implementation details.

Java commonly expresses abstraction with interfaces and abstract classes.

## Abstract classes

An abstract class cannot be instantiated directly. It can define shared state and implementation, as well as abstract methods that subclasses must implement:

```java
abstract class Shape {
    abstract double area();

    void printArea() {
        System.out.println(area());
    }
}

class Circle extends Shape {
    private final double radius;

    Circle(double radius) {
        this.radius = radius;
    }

    @Override
    double area() {
        return Math.PI * radius * radius;
    }
}
```

`Shape` defines a common contract and shared behavior. `Circle` supplies the missing implementation.

An abstract class may have constructors, fields, concrete methods, and abstract methods. A concrete subclass must implement all inherited abstract methods, unless it too is declared abstract.

## Choosing the right abstraction

Use an abstract class when related classes share state or implementation and need a common base. Use an interface when you want to describe a capability that potentially unrelated classes can implement. A class can extend only one class but implement multiple interfaces.

For interfaces, see [Interfaces](06-Interfaces.md).

## Designing a useful abstraction

- Expose operations that callers need, not internal steps.
- Keep each operation's meaning clear and consistent.
- Avoid adding methods that callers do not need.
- Prefer a small contract that is easy to implement and test.

## Common mistakes

- Trying to instantiate an abstract class with `new`.
- Declaring a method abstract but forgetting to implement it in a concrete subclass.
- Making an abstraction so broad that unrelated concepts are forced into it.
- Assuming abstraction always requires inheritance; interfaces and composition can also hide implementation details.
