# Set

A `Set<E>` stores unique elements: adding an element that is already present does not create a duplicate. Use a set when membership and uniqueness matter more than positions.

## Create and use a set

```java
import java.util.HashSet;
import java.util.Set;

Set<String> tags = new HashSet<String>();
tags.add("java");
tags.add("beginner");
tags.add("java"); // already present; set remains unique

System.out.println(tags.size()); // 2
System.out.println(tags.contains("java")); // true
```

## Choosing an implementation

- `HashSet`: common choice; does not promise iteration order.
- `LinkedHashSet`: preserves insertion order.
- `TreeSet`: stores elements in sorted order.

Elements in a `TreeSet` must be comparable, or the set must be given a comparator.

## Equality and hashing

`HashSet` uses `equals()` and `hashCode()` to identify duplicates. For a custom class, implement these consistently. If two objects are equal, they must return the same hash code.

Do not change fields used by equality or hashing while an object is stored in a hash-based set; later membership checks may behave unexpectedly.

## Set operations

The `Set` interface supports operations such as `add`, `remove`, `contains`, and `size`. You can also build mathematical-style operations:

```java
Set<Integer> first = new HashSet<Integer>();
first.add(1);
first.add(2);

Set<Integer> second = new HashSet<Integer>();
second.add(2);
second.add(3);

Set<Integer> union = new HashSet<Integer>(first);
union.addAll(second); // {1, 2, 3}

Set<Integer> intersection = new HashSet<Integer>(first);
intersection.retainAll(second); // {2}
```

Hash-based set iteration order is unspecified; do not write code that depends on it.

## Common mistakes

- Expecting duplicates to be retained.
- Assuming a `HashSet` is sorted or preserves insertion order.
- Forgetting that custom objects need correct `equals()` and `hashCode()` for logical uniqueness.
- Assuming `TreeSet` can accept any object without an ordering rule.
