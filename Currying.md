# Currying
```javascript
//Normal
function addThreeNumbers = (a, b, c) => {
  return a + b + c;
}

//Curried

const greetDeeplyCurried = function(greeting) {
  return function(separator) {
    return function(name)  {
       return function(emphasis){
        console.log(greeting + separator + name + emphasis);
      };
    };
  };
};

greetDeeplyCurried("Hello")(" ")("AJ")("!");

//Currying with the Arrow Notation

const map = array => {
  return f => {
  const result = [];
  for (const ele of array) {
    result.push(f(ele));
  }
  return result;
}
}

map(arr)(addThree)
```
