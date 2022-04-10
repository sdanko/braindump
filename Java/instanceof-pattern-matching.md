# `instanceof` With Pattern Matching

`instanceof` operator is used to determine if a given Java object is an instance of a given class, superclass or interface. It is also referred to as a type comparison operator.
Since Java 14, this operator has been extended with pattern matching functionality. If you see something like this:


```
Object strObject = "test";

if(strObject instanceof String str) {
    System.out.println(str.substring(0,2));
}
``` 

This means that if strObject references an object of type String, the str variable will be bound to that object, but as a cast to String. This way,  inside the if-statement it is no longer necessary to explicitly cast the strObject variable to a String.
