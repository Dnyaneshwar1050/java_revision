# Loops

Loops repeat code. Choose the loop that makes the stopping condition and iteration easiest to understand.

## `for` loop

Use a `for` loop when you know how to initialize, test, and update a counter:

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

This prints `0` through `4`. The three parts are initialization (`int i = 0`), condition (`i < 5`), and update (`i++`).

## `while` loop

Use `while` when the number of repetitions depends on a condition:

```java
int attempts = 0;
while (attempts < 3) {
    System.out.println("Attempt " + attempts);
    attempts++;
}
```

Check that something inside the loop eventually makes the condition false, or the loop may never stop.

## `do-while` loop

A `do-while` loop always runs its body at least once:

```java
int number = 1;
do {
    System.out.println(number);
    number++;
} while (number <= 3);
```

The semicolon after the condition is required.

## Enhanced `for` loop

Use it to visit every item in an array or collection:

```java
int[] scores = {80, 95, 72};
for (int score : scores) {
    System.out.println(score);
}
```

This is convenient when you do not need the index. Use an indexed loop when you need positions or need to update array elements.

## `break` and `continue`

- `break` exits the nearest loop.
- `continue` skips to the next iteration.

Use them sparingly; a clear loop condition is often easier to follow.

## Nested loops

A loop inside another loop is useful for grids and pairs of values:

```java
for (int row = 1; row <= 2; row++) {
    for (int column = 1; column <= 3; column++) {
        System.out.println(row + "," + column);
    }
}
```

The inner loop runs fully for every outer-loop iteration.

## Common mistakes

- Off-by-one errors: decide whether the endpoint is included (`<=`) or excluded (`<`).
- Forgetting to update a `while` loop's state, causing an infinite loop.
- Using `i <= array.length`, which accesses one past the last index. The final valid index is `array.length - 1`.
- Modifying a counter in multiple places without a clear reason.
