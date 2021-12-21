### Closures and Scopes

Closure: a paradigm that allows for a function to access and manipulate variables that are external to that function.

- Closures allow a function to access all the variables, as well as other functions, that are in scope when the function itself is defined.

Scope: the visibility of identifiers in certain parts of a program.

- A scope if a part of the program in which a certain name is bound to a certain variable.

```
var outerValue = "samurai";
var later;

function outerFunction(){
  var innerValue = "ninja";

  function innerFunction(){
    assert(outerValue === "samurai", "I can see the samurai.");
    assert(innerValue === "ninja", "I can see the ninja.")
  }

  later = innerFunction;
}

outerFunction();

later();
```

- When we declare `innerFunction` inside the outer function, not only is the function declaration defined, but a closure is created that encompasses the function definition as well as all variables in scope _at the point of function definition_.

- Closures create a safety bubble of the function and the variables in scope at the point of the function's definition, so that the function has all it needs to execute. This bubble stays around as long as the function does.

- Closures cause overhead as in order to keep the information around, you have to do so in memory until it is no longer needed (and safe to be garbage collected), or until the page unloads.

## Practical Uses

1. Mimicking private variables
2. Using closures with callbacks
   - Remember that closures get private bubbles of these variables

## Tracking code execution

- Fundamental unit of execution is a function
- 2 types of JS code:
  1. Global code placed outside of all functions
  2. Function code contained in functions
- When code is being executed by the JS engine, each statement is executed in a certain `execution context`
- 2 types of execution contexts:
  1. Global execution context
  2. Function execution context
- Only 1 global execution context whereas a new function execution context is created on each function invocation
- The call stack is what allows for the internals to keep track of function invocations

Identifier resolution: process of figuring out which variable a certain identifier refers to. The execution context does this via the lexical environment.

## Lexical environment

Lexical environment: internal JS engine construct used to keep track of the mapping from identifiers to specific variables

Separate identifier mappings: function, block of code, or the catch part of a try-catch statement

The outer environment of a JS invocation is stored in the internal `[[Environment]]` property.

## JS Variables

- Variables differ in mutability and their relationship toward the lexical environment

- const is immutable whereas var and let are not

### How does const work?

- A const “variable” is similar to a normal variable, with the exception that we have to provide an initialization value when it’s declared, and we can’t assign a completely new value to it afterward.

- We cannot re-assign but we can modify, as is the case with objects for example

### var

- Variables declared with `var` are always registered in the closest function or global lexical environment without paying any attention to blocks.

## The process of registering identifiers

1. First phase activated whenever a new lexical environment is created. Code is not executed, but the JS engine visits and registers all declared variables and functions within the current lexical environment.
2. Second phase:
   - Does a lot of other stuff too long to type :)

- Function declarations are hoisted while expressions and arrow functions are not
