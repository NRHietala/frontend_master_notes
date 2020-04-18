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
**Closure**- when a function carries data like a variable when stored in the global memory to be used later.

**Memoization**- an optimization technique where you cache previously computed results, and return the cached result when the same computation is needed again.

**Lexical Enviornment**- what a piece of data carries when stored in the global memory.

**Function Decoration**- When you store code in a function's lexical enviornment that has been returned to the global memory.

**PLSRD**- Persistent Lexical Scope Referenced Data (Backpack). JS, being a statically scoped (lexical scope) language, depends upon the lexical enviornment of a function to reference the data in the global memory.

**COVE**- Closed over "Variable Environment".

**Mutliple Closure Instances**- function definitions only use one unique backpack. If a function is defined twice, it will be a different backpack for both function definitions

Ultimately, Closures give our functions persistent memories, which is useful in helper functions like "once" & "memoize", iterators & generators, module pattern, and asynch JS.

Module Pattern- Preserve state for the life of an application without polluting the global namespace

```javascript
//Once
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

//After
function after(count, func) {
  	let times = 1;	
  	return () => {
  	if (times < count) {
      times++;
    } else {
      return func();
    }
  }
}

//Delay
function addTwo(num) {
  console.log(num + 2);
}
function delay(func, wait, num) {
  setTimeout(func, wait, num)
}

delay(addTwo, 1000, 2)

//rollCall
function rollCall(names) {
  let roll = 0
  return () => {
    if (roll < names.length){
    console.log(names[roll]);
    roll++
    }else {
      console.log("Everyone Accounted for!")
    }
  }
}

//saveOutput
function saveOutput(func, magicWord) {
  const obj = {}
  return (n) => {
    if (n === magicWord) {
      return obj
    } else {
      const val = func(n)
      obj[n] = val
      return val
    }
  }
}

//cycleIterator
function cycleIterator(array) {
	let count = -1;
  return () => {
    	if (count < array.length-1) {
        count++;
    		return array[count];
      } else {
        count = -1;
        count++;
        return array[count]
      }
 	 }
  }
```
## Asynchronous JS
JavaScript is not used by the browser features. It is used as an interface with them, which includes DevTools, Timer, Sockets, Console, Network Requests, HTML DOM, and others.

Example is the setTimeout(). It interfaces with the timer that is built into the web browser, but not itself a part of JavaScript.

Another example is document(). It interfaces with the HTML DOM. Fetch => Network Requests. Console => the Console.
```javascript

```
## Promises
```javascript

```
## Classes & Prototypes
```javascript

```
