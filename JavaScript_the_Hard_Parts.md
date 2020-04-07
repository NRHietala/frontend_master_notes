# The Hard Parts
## JS Principles
### Notes
*Reminder: JS is single threaded(it can only run 1 execution context at a time, no matter what)*
**Execution Context**- created to run a function, and contains 2 parts (memory and thread of execution)
**Parameter**- the input name in a function
**Argument**- the actual value assigned to the parameter name
**Call Stack**- the structure that keeps track of what is being run. It operates as a "last in, first out" (think stack of plates)

## Functions & Callbacks
# Notes
**Parameterizing Behavior**- when you take a block of code and make it available without executing it.
**Higher Order Function**- takes another function as input and/or returns a function as output 
**Callback Function**- the function we insert into the higher-order function
**Pair Programming**- Collaboration with other engineers to solve problems. Not a "Stackoverflower", who copies and pastes code, nor a "Researcher", who avoids blocks by reading everything they can find on the block/bug. (a nice balance between the two) 

## Closure
**Closure**- when a function carries data like a variable when stored in the global memory to be used later
**Memoization**- an optimization technique where you cache previously computed results, and return the cached result when the same computation is needed again.
**Lexical Enviornment**- what a piece of data carries when stored in the global memory
```javascript
const once = f => {
  let hasRun = false;
  const t = (num) => {  
    if (hasRun) {
      return;
    } else {
      hasRun = true;
      return f(num);
    }
  }
  return t;
}

const addTwo = num => {
  return num + 2;
}

const r = once(addTwo);
r(4)
r(9)
```
## Asynchronous JS
```javascript

```
## Promises
```javascript

```
## Classes & Prototypes
```javascript

```
