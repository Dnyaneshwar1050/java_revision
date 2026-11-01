# Variables and Data Types

A variable is a named place to store a value. Java is **statically typed**: every variable has a type, and Java checks that type when compiling your program.

## Declaring and assigning

```java
int age;       // declaration: create a variable
age = 20;      // assignment: store a value

String name = "Maya"; // declaration and assignment together
```

The general form is `type name = value;`. A variable can be reassigned if it is not declared `final`:

```java
int score = 10;
score = 15;
```

Use `final` when a local value should not be reassigned:

```java
final double TAX_RATE = 0.18;
```

## Primitive types

Java has eight primitive types:

| Type | Stores | Example |
|---|---|---|
| `byte` | Small whole numbers | `byte level = 3;` |
| `short` | Whole numbers | `short year = 2026;` |
| `int` | Common whole numbers | `int count = 42;` |
| `long` | Large whole numbers | `long population = 8_000_000_000L;` |
| `float` | Decimal values with less precision | `float ratio = 0.5f;` |
| `double` | Common decimal values | `double price = 19.99;` |
| `char` | One UTF-16 code unit | `char grade = 'A';` |
| `boolean` | `true` or `false` | `boolean ready = true;` |

Use `int` for most whole-number work and `double` for general decimal calculations. `float` literals need an `f`; `long` literals may need an `L`.

For money or exact decimal arithmetic, consider `BigDecimal` rather than `float` or `double`, whose binary representation can introduce rounding.

## Reference types

Objects, arrays, and strings are reference types. A reference variable holds a reference to an object, or `null` if it refers to no object.

```java
String city = "Pune";
String missing = null;
int[] numbers = {2, 4, 6};
```

`String` is an object type, not a primitive. Strings are immutable: operations such as `toUpperCase()` return a new string rather than changing the original.

## Type conversion

Some conversions are automatic when no information is lost:

```java
int items = 5;
double exactItems = items; // widening conversion: 5.0
```

A narrowing conversion requires an explicit cast and may lose information:

```java
double measurement = 4.8;
int wholePart = (int) measurement; // 4; fractional part is discarded
```

Convert text to numbers with parsing methods:

```java
int quantity = Integer.parseInt("12");
double temperature = Double.parseDouble("21.5");
```

Invalid numeric text causes `NumberFormatException`; validate or handle it when input is not trusted.

## Operators and expressions

```java
int total = 3 + 4 * 2;  // 11: multiplication happens first
int remainder = 10 % 3; // 1
boolean adult = age >= 18;
```

Parentheses make intent clear: `(3 + 4) * 2`. The `+` operator adds numbers but joins strings when either operand is a string:

```java
String message = "Age: " + age;
```

## Scope and initialization

A local variable exists only inside the block where it is declared. Unlike fields, local variables do **not** get a default value; assign one before reading it.

```java
int result = 0;
if (age >= 18) {
    result = 1;
}
System.out.println(result);
```

Object fields have defaults such as `0`, `false`, or `null`, but explicitly initializing fields often makes intent clearer.

## Common mistakes

- Use `=` to assign and `==` to compare primitive values.
- Compare strings with `.equals()`, not `==`: `name.equals("Maya")`.
- Integer division discards the fractional part: `5 / 2` is `2`; use `5.0 / 2`.
- A variable's declared type limits which values it can hold.
- Avoid unclear names such as `x` outside short mathematical expressions.
