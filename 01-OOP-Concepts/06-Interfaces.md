# Interfaces

An interface defines a contract: a set of operations a class agrees to provide. It lets code depend on a capability rather than a specific implementation.

## Declare and implement an interface

```java
interface Printable {
    void print();
}

class Invoice implements Printable {
    @Override
    public void print() {
        System.out.println("Printing invoice");
    }
}
```

Interface methods without a body are implicitly `public abstract`, so the implementation must be `public`. Use `@Override` to catch mistakes.

```java
Printable document = new Invoice();
document.print();
```

The caller can use any object that implements `Printable`, without needing to know its concrete class.

## Implementing multiple interfaces

A class can implement more than one interface:

```java
interface Saveable {
    void save();
}

class Document implements Printable, Saveable {
    public void print() { }
    public void save() { }
}
```

This is useful for combining independent capabilities without creating a deep class hierarchy.

## Interface fields and methods

Fields declared in an interface are constants (`public static final`). Interfaces may also contain:

- `default` methods with a body, which implementing classes may inherit or override.
- `static` methods, called using the interface name.
- `private` helper methods in modern Java to share code among interface methods.

Use these features deliberately; an interface's main purpose is usually to define a clear contract.

## Interface or abstract class?

| Choose an interface when... | Choose an abstract class when... |
|---|---|
| You are describing a capability or contract. | Related subclasses share state or implementation. |
| Unrelated classes may implement it. | You need constructors or instance fields in the base. |
| A class may need several contracts. | A single shared base class is a natural model. |

## Common mistakes

- Implementing a method without `public`.
- Assuming an interface can be constructed directly.
- Using an interface just to rename one implementation without a useful contract.
- Putting mutable instance state in an interface; interfaces cannot have ordinary instance fields.
