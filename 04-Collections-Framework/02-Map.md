# Map

A `Map<K, V>` stores associations between keys and values. Each key is unique; different keys may have the same value. A map is useful when you want to look up information by a key rather than by a numeric position.

## Create and use a map

```java
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> scores = new HashMap<String, Integer>();
scores.put("Asha", 90);
scores.put("Ravi", 84);

System.out.println(scores.get("Asha")); // 90
```

Adding a value with an existing key replaces the old value:

```java
scores.put("Asha", 95);
```

## Check for a key and handle missing values

`get(key)` returns `null` when no mapping exists (and also when the key is explicitly mapped to `null`). Prefer `containsKey` if that distinction matters:

```java
if (scores.containsKey("Mina")) {
    System.out.println(scores.get("Mina"));
}
```

For a simple fallback:

```java
int score = scores.getOrDefault("Mina", 0);
```

## Iterate through entries

```java
for (Map.Entry<String, Integer> entry : scores.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
```

This is generally clearer and more efficient than looking up each value again by key.

## Choosing an implementation

- `HashMap`: common choice; does not promise iteration order.
- `LinkedHashMap`: preserves insertion order.
- `TreeMap`: keeps keys sorted according to their natural order or a comparator.

## Keys and equality

Map keys are compared using `equals()` and `hashCode()`. If you create a custom key class, implement both consistently: objects that are equal must have the same hash code. Do not change a key in a way that affects equality or hashing while it is stored in a map.

## Common mistakes

- Assuming a `HashMap` keeps insertion order.
- Assuming duplicate keys create multiple entries; a later `put` replaces the earlier mapping.
- Unboxing a missing `Integer` value, which can cause a `NullPointerException`.
- Using a mutable object as a key and then changing fields used by `equals()` or `hashCode()`.
