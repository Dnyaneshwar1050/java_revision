# Try-Catch and Exceptions

An exception represents an event that interrupts the normal flow of a program. Java uses exceptions to report problems such as invalid input, missing files, or failed operations.

## Handle an exception

```java
try {
    int number = Integer.parseInt("not a number");
    System.out.println(number);
} catch (NumberFormatException exception) {
    System.out.println("Please provide a whole number.");
}
```

Put the operation that may fail in `try`. A matching `catch` handles the exception. Catch the most specific exception you can handle meaningfully.

## Checked and unchecked exceptions

- **Checked exceptions** must be caught or declared with `throws`, for example `IOException`.
- **Unchecked exceptions** are subclasses of `RuntimeException`; the compiler does not require handling them. Examples include `NullPointerException` and `IllegalArgumentException`.

```java
static String readFile(String path) throws java.io.IOException {
    byte[] bytes = java.nio.file.Files.readAllBytes(
            java.nio.file.Paths.get(path));
    return new String(bytes, java.nio.charset.StandardCharsets.UTF_8);
}
```

The caller must handle or declare the checked `IOException`.

## `finally` and try-with-resources

`finally` normally runs whether the operation succeeds or fails, and is commonly used for cleanup. For resources that implement `AutoCloseable`, prefer try-with-resources:

```java
try (java.io.BufferedReader reader =
        java.nio.file.Files.newBufferedReader(
                java.nio.file.Paths.get("notes.txt"))) {
    System.out.println(reader.readLine());
}
```

The reader is closed automatically, including when an exception occurs.

## Propagate or handle?

Catch an exception when you can recover, add useful context, or report a clear message. Otherwise, let it propagate by declaring it with `throws`. Do not catch an exception and silently ignore it.

## Common mistakes

- Catching `Exception` broadly when a specific exception is expected.
- Leaving an empty `catch` block, hiding failures.
- Using exceptions for ordinary decisions that are better expressed with conditions.
- Printing only a vague message and losing information needed to diagnose a failure.
- Catching an exception and then continuing as if the failed operation succeeded.
