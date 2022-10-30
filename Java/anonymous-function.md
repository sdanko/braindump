# Anonymous function

The anonymous function was introduced into Java in version 8. It is also called lambda because the idea and a
notation for it was first used in Alonzo Church’s lambda calculus, or λ-calculus, in the 1930s as formal system for
expressing computations.

Consider these two lines of Java code:
```
int sum(int c, int d) {return c + d;}
(c, d) -> c + d
```

The first is a conventional function declaration. The second is an expression whose evaluation yields an equivalent
anonymous function —anonymous because the function is not given a name. The list of parameters is there (though
their types need not be given), the function body is there (though in this case braces are not needed), but the function
name is not there. Also, keyword return is not needed. The body is an expression, and its value is returned.

In certain circumstances, you could assign the anonymous function to a variable:
```
add= (c, d) -> {c + d};
```

and then call it, using:
```
add.apply(3, 4);
```
In functional programming languages, anonymous functions are easy to write and understand. Because of the
way anonymous functions are added to Java in version 8, their introduction is more complex. For example, variable
add in the above paragraphs has type:
```
BiFunction<Integer, Integer, Integer>
```
which means that it is a function that has two Integer parameters and returns an Integer.

Lambda expression and method reference are two different ways of writing anonymous function.

## Method reference

Method reference was introduced to remove the verbosity of closures in Java. Any method from 
java.lang.Function can be used as a method reference. It is not necessary to use new keyword while 
using method references. There is a performance advantage of using method reference over using 
lambda expressions. 

Method reference can be defined as some special form of the lambda expression. 
It is mainly because, in this case, the lambda expressions are not involved in doing any task, 
but rather it is involved in invoking the methods which exist.

For example, if the lambda expression looks like the way as shown below:
```
str -> System.out.println(str)
```
With method reference we can write it like this:
```
System.out::println
```

`::` operator is used in the method reference to separate the object or the class from the method’s name. 

There are several types of a method reference in Java that are allowed in Java 8:
- Reference to static methods: The static methods in a code can be referred to from a class.
- Reference to instance method of particular object.
- Reference to instance method of an arbitrary object of any particular type.
- Reference to a constructor.
