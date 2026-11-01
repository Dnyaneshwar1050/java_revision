# Encapsulation

Encapsulation keeps an object's data and the rules for using that data together. It protects the object's state so callers cannot put it into an invalid condition.

The usual starting point is to make fields `private` and provide meaningful public methods.

## Protecting state

```java
class BankAccount {
    private double balance;

    BankAccount(double startingBalance) {
        if (startingBalance < 0) {
            throw new IllegalArgumentException("Starting balance cannot be negative");
        }
        balance = startingBalance;
    }

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount <= 0) {
            throw new IllegalArgumentException("Deposit must be positive");
        }
        balance += amount;
    }
}
```

Callers cannot directly set `balance` to a negative number. The `deposit` operation enforces a rule before changing it.

## Getters and setters

A getter returns information; a setter changes a field. They are methods, not a requirement for every field:

```java
public String getName() {
    return name;
}
```

Do not add a setter automatically if changing a value should be controlled or disallowed. A method such as `deposit` expresses intent and can validate the operation better than `setBalance`.

## Invariants

An invariant is a rule that should remain true for an object, such as "balance is non-negative." Check inputs at the point where state changes, so every caller follows the same rule.

## Defensive copying

Returning a mutable internal object can let callers change state without using the class's methods. Return a copy when the object must remain protected:

```java
class Team {
    private final java.util.List<String> members =
            new java.util.ArrayList<String>();

    public java.util.List<String> getMembers() {
        return new java.util.ArrayList<String>(members);
    }
}
```

The returned list is a shallow copy. If its elements are themselves mutable objects, additional protection may be needed.

## Benefits

- Rules can be changed internally without changing callers.
- Invalid updates can be rejected at one well-defined boundary.
- Callers see a small, meaningful API instead of implementation details.
- Testing and maintenance are easier because state changes are controlled.

## Common mistakes

- Making fields public and hoping every caller follows the rules.
- Adding setters that allow invalid values.
- Returning internal mutable lists or arrays without considering who can modify them.
- Assuming `private` means secure against all threats; it is an object-design access rule, not a security boundary.
