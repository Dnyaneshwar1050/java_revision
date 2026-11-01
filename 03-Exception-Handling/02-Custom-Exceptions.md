# Custom Exceptions

A custom exception gives a failure a name that communicates what went wrong in your application. Create one when the standard exceptions do not describe an important domain-specific condition.

## Create a checked exception

Extend `Exception` when callers should be required to handle or declare the condition:

```java
class InsufficientFundsException extends Exception {
    InsufficientFundsException(String message) {
        super(message);
    }
}
```

Use it from an operation:

```java
class Account {
    private double balance;

    void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException("Not enough funds");
        }
        balance -= amount;
    }
}
```

The caller must handle the exception or declare it with `throws`.

## Create an unchecked exception

Extend `RuntimeException` when the caller is not required by the compiler to catch the problem:

```java
class InvalidOrderException extends RuntimeException {
    InvalidOrderException(String message) {
        super(message);
    }
}
```

Unchecked exceptions are often appropriate for invalid arguments or violated preconditions. Prefer standard exceptions such as `IllegalArgumentException` when they already express the problem clearly.

## Throwing and handling

`throw` creates and raises an exception. `throws` declares that a method may pass an exception to its caller:

```java
throw new InsufficientFundsException("Not enough funds");
```

These are different: `throw` is an action; `throws` appears in a method signature.

## Good exception design

- Use a name that identifies the specific failure.
- Include a useful message, but do not expose secrets or sensitive data.
- Preserve the original cause when translating an exception: `new SomeException("Context", cause)`.
- Do not use custom exceptions for normal control flow.
- Keep exceptions focused; avoid creating many nearly identical types without a real need.

## Common mistakes

- Forgetting to call `super(message)`, so the useful message is lost.
- Declaring a checked exception without a reason for callers to handle it.
- Catching your custom exception and discarding it.
- Using `throws` when you intended to raise the exception with `throw`.
