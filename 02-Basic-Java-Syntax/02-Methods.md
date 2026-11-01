# Methods

A method is a named block of code that performs a task. Methods help avoid repetition and make programs easier to understand.

## Method structure

```java
static int add(int left, int right) {
    int total = left + right;
    return total;
}
```

- `static` means this example method belongs to its class rather than a particular object.
- `int` is the return type.
- `add` is the method name.
- `left` and `right` are parameters.
- `return` sends a result back to the caller.

Call it with arguments:

```java
int answer = add(3, 4); // answer is 7
```

The parameter types, order, and count must match the method declaration.

## `void` methods

Use `void` when a method performs an action but does not return a value:

```java
static void printGreeting(String name) {
    System.out.println("Hello, " + name);
}
```

## Method overloading

Methods can share a name if their parameter lists differ:

```java
static int multiply(int a, int b) {
    return a * b;
}

static double multiply(double a, double b) {
    return a * b;
}
```

Changing only the return type is not enough to overload a method. Java chooses an overload based on the arguments at the call site.

## Parameters and return values

Java passes arguments **by value**. For primitive values, the method receives a copy. For an object, it receives a copy of the reference; it can use that reference to change the object's state, but reassigning the parameter does not reassign the caller's variable.

```java
static void updateFirst(int[] values) {
    values[0] = 99; // changes the array object
}
```

Keep methods focused. A method that calculates a value is often clearer when it returns the value instead of printing it internally.

## Local variables and scope

Variables declared inside a method or block are local to that region:

```java
static int square(int value) {
    int result = value * value;
    return result;
}
```

`result` cannot be used outside `square`.

## The `main` method

For a simple Java application, the runtime starts at `main`:

```java
public static void main(String[] args) {
    int sum = add(2, 5);
    System.out.println(sum);
}
```

`args` contains command-line arguments as strings. `static` lets the runtime call `main` without first constructing an object.

## Common mistakes

- Forgetting to return a value from a non-`void` method.
- Returning a value that does not match the declared return type.
- Confusing a parameter (declared by the method) with an argument (provided by the caller).
- Expecting a method to change a caller's primitive variable.
- Repeating the same logic instead of extracting a focused helper method.
