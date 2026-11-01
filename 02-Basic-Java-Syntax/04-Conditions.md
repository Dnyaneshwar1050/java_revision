# Conditions

Conditions let a program choose what to do based on a boolean expression. A condition evaluates to either `true` or `false`.

## Comparison and logical operators

| Operator | Meaning |
|---|---|
| `==`, `!=` | equal to, not equal to |
| `<`, `<=`, `>`, `>=` | numeric comparisons |
| `&&` | AND: both sides must be true |
| `||` | OR: at least one side must be true |
| `!` | NOT: reverses a boolean |

```java
int age = 20;
boolean canVote = age >= 18;
boolean eligible = age >= 18 && age <= 100;
```

`&&` and `||` short-circuit: Java may skip the right side when the result is already determined. This can guard a potentially unsafe operation:

```java
if (name != null && name.length() > 0) {
    System.out.println(name);
}
```

## `if`, `else if`, and `else`

```java
int score = 82;
if (score >= 90) {
    System.out.println("A");
} else if (score >= 75) {
    System.out.println("B");
} else {
    System.out.println("Keep practicing");
}
```

Conditions are checked from top to bottom. Once one branch matches, the remaining branches are skipped.

Use braces even for one-line branches; they reduce mistakes when code changes later.

## `switch`

Use `switch` when comparing one value with several discrete options:

```java
int day = 2;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Another day");
}
```

In the traditional `switch` statement, `break` prevents execution from continuing into the next case. `default` handles values not covered by another case.

## Ternary operator

For a short expression that chooses between two values:

```java
String status = age >= 18 ? "adult" : "minor";
```

Avoid deeply nested ternary expressions; an `if` statement is clearer.

## Comparing strings

`==` compares primitive values, but for objects it checks whether references identify the same object. To compare string contents, use `.equals()`:

```java
String answer = "yes";
if ("yes".equals(answer)) {
    System.out.println("Confirmed");
}
```

Writing the known non-null string first also avoids a null dereference if `answer` is `null`.

## Common mistakes

- Writing `=` instead of `==` in a comparison.
- Comparing string contents with `==`.
- Forgetting `break` in a traditional `switch`.
- Making conditions so complex that their meaning is hard to verify; use named boolean variables or helper methods.
