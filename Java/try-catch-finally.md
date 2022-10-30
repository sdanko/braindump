# Try Catch Finally

## The try Block

The first step in constructing an exception handler is to enclose the code that might throw an 
exception within a try block. In general, a try block looks like the following:

```
try {
code
}
catch and finally blocks . . .
```

The segment in the example labeled code contains one or more legal lines of code that could throw an exception.

## The catch Blocks

You associate exception handlers with a try block by providing one or more catch blocks directly 
after the try block. No code can be between the end of the try block and the beginning of the first 
catch block.

```
try {

} catch (ExceptionType name) {

} catch (ExceptionType name) {

}
```

Each catch block is an exception handler that handles the type of exception indicated by its argument.
The argument type, `ExceptionType`, declares the type of exception that the handler can handle and 
must be the name of a class that inherits from the Throwable class. The handler can refer to the
exception with name.

The catch block contains code that is executed if and when the exception handler is invoked. 
The runtime system invokes the exception handler when the handler is the first one in the call
stack whose ExceptionType matches the type of the exception thrown. The system considers it a 
match if the thrown object can legally be assigned to the exception handler's argument.

In Java SE 7 and later, a single catch block can handle more than one type of exception. 
This feature can reduce code duplication and lessen the temptation to catch an overly broad exception.

In the catch clause, specify the types of exceptions that block can handle, and separate each
exception type with a vertical bar (|):

```
catch (IOException|SQLException ex) {
logger.log(ex);
throw ex;
}
```

## The finally Block

The finally block always executes when the try block exits. This ensures that the finally block is 
executed even if an unexpected exception occurs. But finally is useful for more than just exception
handling — it allows the programmer to avoid having cleanup code accidentally bypassed by a return,
continue, or break. Putting cleanup code in a finally block is always a good practice, even when 
no exceptions are anticipated.

It is bad practice to use return statements in the finally block.  it will override any other return from the regular block.
That is, the following block would return false:

```
try { return true; } finally { return false; }
```

It is also bad practice to throw exceptions from the finally block.
