# Type conversion and coercion

Type conversion is explicit conversion of values from one data type to another (such as strings to numbers). Type coercion is the automatic or implicit conversion of values from one data type to another. It usually happens when you apply operators to values of different types. There are three types of conversion in JavaScript:
- to string
- to boolean
- to number

## To String

To explicitly convert values to string we can apply `String()` function.

```
String(123)                   // '123'
String(-12.3)                 // '-12.3'
String(null)                  // 'null'
String(undefined)             // 'undefined'
String(true)                  // 'true'
String(false)                 // 'false'
String([])                    // ''
String({})                    // '[object Object]'
``` 

You can also use `toString()` method. It will throw `TypeError` for `null` and `undefined` values.

```
const num1 = 123;
num1.toString(); // '123'

const num2 = NaN;             
num2.toString();  // 'NaN'

const num3 = null;             
num2.toString(); // TypeError

let num4;             
num4.toString(); // TypeError
``` 

There are also 3 methods available for converting numbers to strings:
- [`toExponential()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toExponential)
- [`toFixed()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed)
- [`toPrecision()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toPrecision)

Coercion is triggered by the binary `+` operator, when any operand is a string:

```
'1'  + 2  // '12'
1 + '2' + true // '12true'
1 + '2' + 3 + undefined // '123undefined'
'2' + null // '2null'
'2' + 3 + NaN // '23NaN'
``` 

## To Boolean

`Boolean()` function is used for explicit conversion to boolean values. Implicit conversion happens in logical context(`if (2) { ... } `), or is triggered by logical operators(`||`, `&&`, `!`).

Here is the list of falsy conversion values:

```
Boolean('')           // false
Boolean(0)            // false     
Boolean(-0)           // false
Boolean(NaN)          // false
Boolean(null)         // false
Boolean(undefined)    // false
Boolean(false)        // false
``` 
Any other value is converted to `true`, including object, function, Array, Date, user-defined type, and so on. Empty objects and arrays are truthy values also.

## To Number

`Number()` function is used for explicit conversion to number values. These are the examples for primitive values:

```
Number(null)                   // 0
Number(undefined)              // NaN
Number('')                     // 0
Number(true)                   // 1
Number(false)                  // 0
Number(' 12 ')                 // 12
Number('-12.34')               // -12.34
Number('\n')                   // 0
Number(' 12s ')                // NaN
Number(123)                    // 123
``` 

When converting a string to a number, the engine first trims leading and trailing whitespace, `\n`, `\t` characters, returning `NaN` if the trimmed string does not represent a valid number. If string is empty, it returns 0.

There are also 2 functions available for parsing strings to numbers:
- [`parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)
- [`parseFloat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseFloat)

Implicit conversion is triggered in multiple cases:
- comparison operators (`>`, `<`, `<=`,`>=`)
- bitwise operators ( `|`,  `&`, `^`, `~`)
- arithmetic operators (`-`,  `+`,  `*`, `/`,  `%` ). Binary `+` operator does not trigger numeric conversion, when any operand is a string.
- unary `+` operator
- loose equality operator `==`

When applying `==` to `null` or `undefined`, numeric conversion does not happen. `null` equals only to `null` or `undefined`, and does not equal to anything else.

```
null == 0               // false, null is not converted to 0
null == null            // true
undefined == undefined  // true
null == undefined       // true
``` 

## Type conversion for objects

When it comes to type conversion for objects, engine first needs to convert the object to primitive value and then its converted to the final type. As for primitive types, there are only three types of conversion: string, numeric and boolean.

The simplest case is boolean conversion, since all non-primitive types are converted to `true`(this includes empty objects and arrays).

When numeric and string conversion is taking place, there are 3 types(also called *hints*):
- **string**  - for alert and other operations that need a string
- **number** -  for math operators
- **default** - occurs in rare cases when the operator is “not sure” what type to expect. Built-in objects implement **default** same as **number**, except `Date` objects.

The specification describes explicitly which operator uses which hint.

The conversion algorithm is:
1.  Call `obj[Symbol.toPrimitive](hint)` if the method exists.
2. Otherwise if hint is **string**: try `obj.toString()` and `obj.valueOf()`, whatever exists.
3. Otherwise if hint is **number** or **default**: try `obj.valueOf()` and `obj.toString()`, whatever exists.

By default, a plain object has following `toString()` and `valueOf()` methods:
- The`toString()` method returns a string `[object Object]`.
- The `valueOf()` method returns the object itself.

Resources:
- https://www.freecodecamp.org/news/js-type-coercion-explained-27ba3d9a2839/
- https://javascript.info/object-toprimitive
