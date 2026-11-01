# Classes and Objects

A **class** describes a kind of thing: the data it stores and the operations it supports. An **object** is one instance created from that class.

For example, `Car` can describe cars in general, while `myCar` is one particular car with its own color and speed.

## Define a class

```java
class Car {
    String color;
    int speed;

    void accelerate(int amount) {
        speed += amount;
    }
}
```

- `color` and `speed` are fields (object state).
- `accelerate` is an instance method (object behavior).
- Each `Car` object has its own field values.

## Create and use an object

```java
Car myCar = new Car();
myCar.color = "blue";
myCar.accelerate(10);
System.out.println(myCar.speed); // 10
```

`new Car()` creates an object. `myCar` is a reference to it. Another `Car` created with `new` is a separate object.

## Constructors

A constructor initializes a new object. Its name matches the class and it has no return type:

```java
class Car {
    String color;
    int speed;

    Car(String color) {
        this.color = color;
        this.speed = 0;
    }
}
```

`this.color` means the field on this object; `color` on the right is the constructor parameter.

Create one with `Car myCar = new Car("blue");`. If you declare no constructor, Java provides a no-argument constructor. Once you declare any constructor, Java does not automatically provide that default constructor.

## Instance members and `static`

Instance fields and methods belong to each object. A `static` member belongs to the class itself and is shared:

```java
class Counter {
    static int created = 0;

    Counter() {
        created++;
    }
}
```

Access a static member using the class name: `Counter.created`. Do not make a field static simply to make it accessible.

## Access modifiers

- `public`: accessible wherever the class is visible.
- `private`: accessible only inside the declaring class.
- `protected`: accessible in the same package and in subclasses (subject to Java's access rules).
- No modifier (package-private): accessible within the same package.

Use `private` fields and expose only the operations callers need; see [encapsulation](03-Encapsulation.md).

## Common mistakes

- Treating a class as an object; a class is a blueprint, an object is an instance.
- Calling an instance method without an object.
- Confusing a constructor with a method: constructors have no return type.
- Making all fields `public`, which makes object state easy to change into invalid values.
