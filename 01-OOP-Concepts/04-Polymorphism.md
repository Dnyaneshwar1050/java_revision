# Polymorphism

Polymorphism means "many forms." In object-oriented Java, code can use a superclass or interface reference while the actual object supplies the behavior.

## Runtime polymorphism: overriding

```java
class Animal {
    void speak() {
        System.out.println("Some sound");
    }
}

class Cat extends Animal {
    @Override
    void speak() {
        System.out.println("Meow");
    }
}
```

```java
Animal pet = new Cat();
pet.speak(); // Meow
```

The reference type (`Animal`) controls which members are available at compile time. The actual object type (`Cat`) determines which overridden instance method runs at runtime.

This lets one method work with many implementations:

```java
static void makeItSpeak(Animal animal) {
    animal.speak();
}
```

Pass a `Cat`, a `Dog`, or another `Animal` subclass without changing `makeItSpeak`.

## Compile-time polymorphism: overloading

Overloaded methods have the same name but different parameter lists:

```java
static int max(int a, int b) {
    return a > b ? a : b;
}

static double max(double a, double b) {
    return a > b ? a : b;
}
```

The compiler selects an overload based on the arguments. Overloading is different from overriding: overriding replaces inherited instance behavior, while overloading provides multiple signatures.

## Upcasting and downcasting

Assigning a subclass object to a superclass reference is an upcast and is safe:

```java
Animal animal = new Cat();
```

Casting down to a subclass is only valid if the object really has that type. Prefer polymorphic methods; if a cast is necessary, check with `instanceof` first:

```java
if (animal instanceof Cat) {
    Cat cat = (Cat) animal;
}
```

An invalid cast throws `ClassCastException`.

## Why it is useful

Polymorphism reduces condition-heavy code. Rather than asking each object what kind it is and choosing behavior externally, call a shared method and let the object's implementation decide what to do.

## Common mistakes

- Expecting a superclass reference to expose subclass-only methods.
- Confusing overload selection (compile time) with override dispatch (runtime).
- Trying to override a `static` method; static methods are hidden, not dynamically dispatched.
- Using many casts instead of a common superclass or interface.
