# Inheritance

Inheritance lets a class reuse and specialize the behavior of another class. The existing class is the **superclass** (parent); the new class is the **subclass** (child).

Use inheritance for a genuine **is-a** relationship. A `Dog` is an `Animal`; a `Car` is not an `Engine`.

## Basic example

```java
class Animal {
    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Woof");
    }
}
```

```java
Dog dog = new Dog();
dog.eat();  // inherited from Animal
dog.bark(); // declared by Dog
```

Java classes have one direct superclass. Every class ultimately derives from `Object`.

## Constructors and `super`

The superclass portion of an object must be initialized before the subclass portion:

```java
class Animal {
    private final String name;

    Animal(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    Dog(String name) {
        super(name);
    }
}
```

`super(name)` calls the superclass constructor and must be the first statement in the constructor. If the superclass has no no-argument constructor, a subclass constructor must explicitly call an available superclass constructor.

## Overriding behavior

A subclass can provide a specialized implementation of an inherited method:

```java
class Animal {
    void speak() {
        System.out.println("Some sound");
    }
}

class Dog extends Animal {
    @Override
    void speak() {
        System.out.println("Woof");
    }
}
```

`@Override` asks the compiler to check that the method really overrides a superclass method. It catches misspellings and mismatched parameter lists.

`super.speak()` can call the superclass implementation from an override.

## What inheritance does not do

- Constructors are not inherited.
- `private` members cannot be accessed directly by subclass code.
- A `final` class cannot be extended; a `final` method cannot be overridden.
- Static methods are hidden rather than overridden; prefer instance methods for polymorphic behavior.

## Prefer composition when appropriate

If one object **has** another object rather than **is** another kind of object, use composition:

```java
class Car {
    private final Engine engine = new Engine();
}
```

Composition often keeps designs more flexible than deep inheritance hierarchies.

## Common mistakes

- Using inheritance only to share a few lines of code when the relationship is not truly "is-a".
- Forgetting that a parent constructor must run first.
- Omitting `@Override` and accidentally creating a different overload.
- Trying to access a superclass's private field directly; expose safe behavior or use a suitable protected/public API.
