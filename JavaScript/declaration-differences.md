# Differences between declarations

|          | **Scope**           | **Activation**   | **Duplicates** | **Global** prop. |
|----------|---------------------|------------------|----------------|------------------|
| const    | Block               | decl. (TDZ)      | ✘              | ✘                |
| let      | Block               | decl. (TDZ)      | ✘              | ✘                |
| function | Block (strict mode) | start            | ✔              | ✔                |
| class    | Block               | decl. (TDZ)      | ✘              | ✘                |
| import   | Module              | same as export   | ✘              | ✘                |
| var      | Function            | start, partially | ✔              | ✔                |

- **Duplicate** describes whether it is allowed to declare a name twice within the same scope.
- **Global prop.** describes if a declaration adds a property to the global object when it is executed in a script (a precursor to modules), in global scope.
- **TDZ** means temporal dead zone.
- **Activation** refers to the point when the variable is accessible. This can be after the declaration(TDZ) or after the start of the scope. `var` is accessible after the start of the scope, but partially, because it returns `undefined` before declaration.
