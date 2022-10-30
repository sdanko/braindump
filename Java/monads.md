# Mondas

A monad is a concept originating from a part of mathematics called category theory. `Stream` and `Optional`
are implementations of this concept. We can view monad as a wrapper that puts our value in some context and allows
us to perform operations, specifically operations that return value wrapped in the same context. Also, we can chain the 
operations in such a manner that the output of an operation at any step is the input to the operation at the next step.

## Monad Laws

Monad has three laws: **Left Identity**, **Right Identity**, and **Associativity**.

### Left Identity

If we create a new monad and bind it to the function, the result should be the same as applying the 
function to the value. 

```
    private static Optional<String> mapper(String input) {
        return input == null ? Optional.empty() : Optional.of(input.toUpperCase());
    }
    
    String x = "Test";
    Optional<String> leftIdentity = Optional.of(x).flatMap(Application::mapper);
    Optional<String> mappedX = mapper("Test");
    assert leftIdentity.equals(mappedX);
    
```

### Right Identity

The result of binding a unit function to a monad should be the same as the creation of a new monad.

```
    Integer x = 5;
    Optional<Integer> rightIdentity = Optional.of(x).flatMap(Optional::of);
    Optional<Integer> wrappedX = Optional.of(x);
    assert rightIdentity.equals(wrappedX);
```

### Associativity

In the chain of function applications, it should not matter how functions are nested.

```
Optional<Long> leftSide = Optional.of(x).flatMap(f).flatMap(g);
Optional<Long> rightSide = Optional.of(x).flatMap(v -> f.apply(v).flatMap(g));
assert leftSide.equals(rightSide);
```

### Implementation

The first thing we need is a parameterized type M<T>, which is a wrapper for our value of type T. Our type must implement two functions:
- of (unit) which is used to wrap our value and has the following signature M<T>(T).
- flatMap (bind) responsible for performing operations. Here we pass a function that operates on value
in our context and returns it with another type already wrapped in context. This method should have
the following signature M<U> (T -> M<U>).


```
import java.util.function.Function;

public final class WrapperMonad<T> {

    private final T value;

    private WrapperMonad(T value) {
        this.value = value;
    }

    static <T> WrapperMonad<T> of(T value) {
        return new WrapperMonad<>(value);
    }

    <U> WrapperMonad<U> flatMap(Function<T, WrapperMonad<U>> function) {
        return function.apply(value);
    }

  	// For sake of asserting in Example
    boolean valueEquals(T x) {
        return value.equals(x);
    }
}
```

Resources: 
- https://dzone.com/articles/what-is-a-monad-basic-theory-for-a-java-developer
