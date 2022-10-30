# Methods

A method in Java or Java Method is a collection of statements that perform some specific task and
return the result to the caller. A Java method can perform some specific task without returning anything. 
Methods in Java allow us to reuse the code without retyping the code. In Java, every method must be part 
of some class that is different from languages like C, C++, and Python. 

## Method Declaration

In general, method declarations has six components :  
1. It defines the access type of the method i.e. from where it can be accessed in your application.
In Java, there 4 types of access specifiers:
   - public: It is accessible in all classes in your application.
   - protected: It is accessible within the class in which it is defined and in its subclass/es
   - private: It is accessible only within the class in which it is defined.
   - default: It is declared/defined without using any modifier. It is accessible within the same class 
   and package within which its class is defined.
2. The return type: The data type of the value returned by the method or void if does not return a value.
3. Method Name: the rules for field names apply to method names as well, but the convention is a little different.
4. Parameter list: Comma-separated list of the input parameters is defined, preceded with their data type, within the enclosed parenthesis.
If there are no parameters, you must use empty parentheses ().
5. Exception list: The exceptions you expect by the method can throw, you can specify these exception(s).
6. Method body: it is enclosed between braces. The code you need to be executed to perform your intended operations.

## Types of Methods

There are two types of methods in Java:
1. Predefined Method: In Java, predefined methods are the method that is already defined in the Java class libraries is known as predefined methods. 
It is also known as the standard library method or built-in method. We can directly use these methods just by calling them in the program at any point. 
2. User-defined Method: The method written by the user or programmer is known as a user-defined method. 
These methods are modified according to the requirement.

