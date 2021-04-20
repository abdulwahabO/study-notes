### Overview of Generics

 Generics provide a type-safe and easy to read way of re-using code for a collection of different _types_. Without generics, re-using code for different _types_ would involve assignments to `Object` references, and casting when dereferencing.

```java
interface Entry<K, V> {
    K getKey();
    V getValue();
}
```

`Entry` is a generic interface definition with two _type parameters_. Below is a generic type invocation of `Entry` with two _type arguments_. `entry` is a known as a _parameterized type_ can itself be a type argument in a generic type invocation.

```java
Entry<String, Double> entry = new Entry<>();
```

See [Raw Types](https://docs.oracle.com/javase/tutorial/java/generics/rawTypes.html)

Non-generic classes can contain generic methods and constructors.

### Bounded Type Parameters

Bounded type parameters are used to restrict the _types_ that can be passed as argument during a generic type invocation. E.g The method declared below will only work for _types_ that implement `Comparable` and extend `Number`. Notice that the type bound lists the concrete class before the interface.

```java
public static <T extends Number, Comparable<T>> boolean isBiggerThan(T a, T b) {
    return a > a;
}
```

Note: Given two non-generic types: `A` which extends `B`. The generic types `Box<A>` and `Box<B>` have no relationship whatsoever regardless of the relationship between `A` and `B`.

Note: You can create a subtype of a generic type by extending or implementing it.

```java
public PairedBox<K, V> extends Box<V> {
    // Logic
}
```

See [Wildcards](https://docs.oracle.com/javase/tutorial/java/generics/wildcards.html)

### Type Erasure

At compile time, all type parameter are replaced with their first bound class/interface, or `Object` if the generic type is unbounded. The `Entry` interface from above becomes:

```java
interface Entry {
    Object getKey();
    Object getValue();
}
```
