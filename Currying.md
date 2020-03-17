# Currying
```javascript
//Normal
const addThreeNumbers = (a, b, c) => {
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

//A Curried Map Using a Curried Reduce

const arr = [1,2,3,4,5,6,7];

const reduce = array => {
  return initialValue => {
    return f => {
      let result = initialValue;
      for (const ele of array) {
        result = f(result, ele);
      }
      return result;
    }
  }
}

const map = array => {
  return f => {
    return reduce(arr)([])((result, ele) => {
      result.push(f(ele));
      return result;
    })
  }
}

map(arr)(num => num + 3)
```
