# List

A `List` is an ordered collection that allows duplicates. Elements have zero-based indexes, so a list is useful when order and position matter.

## Create and use a list

```java
import java.util.ArrayList;
import java.util.List;

List<String> names = new ArrayList<String>();
names.add("Asha");
names.add("Ravi");
names.add("Asha"); // duplicates are allowed

System.out.println(names.get(0)); // Asha
System.out.println(names.size()); // 3
```

The variable uses the interface type `List`; `ArrayList` is one implementation. This makes it easier to replace the implementation later.

For Java 7 and later, the declaration can use the diamond operator: `new ArrayList<>()`.

## Common operations

```java
names.set(1, "Mina");       // replace at index 1
names.remove(0);            // remove item at index 0
boolean found = names.contains("Asha");
```

Accessing or changing an invalid index throws `IndexOutOfBoundsException`. Valid indexes are from `0` to `size() - 1`.

## Iterate over a list

```java
for (String name : names) {
    System.out.println(name);
}
```

For indexed access:

```java
for (int i = 0; i < names.size(); i++) {
    System.out.println(i + ": " + names.get(i));
}
```

Avoid structurally adding or removing items from a list inside an enhanced `for` loop; that can cause `ConcurrentModificationException`. Use an `Iterator` or remove items with a suitable predicate method instead.

## Choosing an implementation

- `ArrayList`: a good default; fast indexed access and iteration.
- `LinkedList`: supports efficient changes at the ends, but indexed access is slow; do not choose it automatically.

## Generics

`List<String>` means this list is intended to contain strings. Generics catch many type mistakes at compile time and avoid manual casts.

Primitive types cannot be generic type arguments. Use wrapper classes such as `Integer` instead of `int`: `List<Integer>`.

## Common mistakes

- Using an index equal to `size()`; the last valid index is `size() - 1`.
- Comparing lists or their contents with `==` when content equality is intended; use `.equals()`.
- Assuming a list automatically prevents duplicates.
- Modifying a list in a loop in a way that invalidates its iterator.
