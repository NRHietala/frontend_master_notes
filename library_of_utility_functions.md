# Library of Utility Functions
## Recreation of the Underscore Library
```javascript
const arr = [1,2,3,4,5,6,7];
const car = [{make: "Ford", model: "Focus", color: "blue", tires: 4}, {miles: 6000, country: "USA"}, {tires: 4, tireBrand: "Firestone"},{interior: "leather", colorOfInterior: "black"}];

const {make, model, color, tires} = car[0];
const {miles,country} = car[1];
const {tireBrand} = car[2];
const {interior, colorOfInterior} = car[3];

const arr2 = [2.1, 5.4, 6.1, 9.3, 2.6, 9.4];
const arr3 = [0, undefined, 1, 2, 6, -3, "", " "];

const library = {
  each: (array,f) => {
    for(const ele of array) {
      f(ele);
    }
  },
  map: (array, f) => {
    const result = [];
    for(let i = 0; i < array.length; i++) {
      result.push(f(array[i], i, array));
    }
    return result;
  },
  //If I do not pass a value for memo, it will assume that the first value is the memo
  reduce: (array, f, memo) => {
    let i = 0;
    if (memo === undefined) {
      memo = array[0];
      i++
    }
    while (i < array.length) {
      memo = f(memo, array[i], i, array);
      i++
    }
    return memo;
  },
  reduceRight: (array, f, memo) => {
    let i = array.length - 1;
    if (memo === undefined) {
      memo = array[0];
      i--
    }
    while (i >= 0) {
      memo = f(memo, array[i], i, array);
      i--
    }
    return memo;
  },
  find: (array, p) => {
    for(const ele of array) {
      if(p(ele)) {
        return ele;
      }
    }
  },
  filter: (array, p) => {
    const result = [];
    for(const ele of array) {
      if(p(ele)) {
        result.push(ele);
      }
    }
    return result;
  },
  where: (array, properties) => {
    const result = [];
    for(const ele of array) {
     let isValid = true;
     for(const [key, value] of Object.entries(properties)) {
       if(ele[key] !== value) {
         isValid = false;
         break;
       }
     }
      if(isValid) {
        result.push(ele);
      }
    }
return result;
},
  reject: (array, p) => {
    const result = [];
    for(const ele of array) {
      if(!p(ele)) {
        result.push(ele);
      }
    }
    return result;
  },
  every: (array, p) => {
    for(const ele of array) {
      if(p(ele) === false) {
        return false;
      }
    }
    return true;
  },
  some: (array, p) => {
    for(const ele of array) {
      if(p(ele)) {
        return true;
      }
    }
    return false;
  },
  contains: (array, value) => {
   return library.some(array, ele => ele === value);
  },
  pluck: (array, propertyName) => {
    const result = [];
    for(const ele of array) {
      if(ele[propertyName] !== undefined) {
        result.push(ele[propertyName]);
      }
    }
    return result;
  },
  //if the list is empty return negative infinity
  //as we loop through it ignores non-numerical values
  max: (array) => {
    if (array.length == 0) {
      return -Infinity;
    }
    let maximumValue = -Infinity;
    for (const ele of array) {
      if(ele > maximumValue) {
        maximumValue = ele;
      }
    }
    return maximumValue;
  },
  min: (array) => {
    if(array.length == 0) {
      return Infinity;
    }
    let minimumValue = Infinity;
    for (const ele of array) {
      if (ele < minimumValue) {
        minimumValue = ele;
      }
    }
    return minimumValue;
  },
  groupBy: (array, f) => {
    const result = {};
    for(const ele of array) {
      const groupKey = f(ele);
      if(result[groupKey] === undefined) {
       result[groupKey] = [ele];
      } else {
        result[groupKey].push(ele);
      }
    }
    return result;
  },
  countBy: (array, f) => {
    const result = [];
    for(const ele of array) {
      const key = f(ele);
      if(result[key] === undefined) {
        result[key] = 1;
      } else {
        result[key]++
      }
    }
    return result;
//   library.countBy(arr, num => {
//   if(num % 2 === 0) {
//     return "even";
//   } else {
//     return "odd";
//   }
// })
  },
  size: (array) => {
    return array.length;
  },
  partition: (array, p) => {
    const result1 = [];
    const result2 = [];
    for(const ele of array) {
      if(p(ele)) {
        result1.push(ele);
      } else {
        result2.push(ele);
      }
    }
    return [result1, result2];
  },
  //truthy = any value that is not 0, "", or undefined. falsy = 0 & undefined
  compact: (array) => {
  const result = [];
  for(const ele of array) {
    if(ele) {
       result.push(ele);
    }
  }
    return result;
}
}

library.compact(arr3);
//Do all except sample, toArray, sortBy, indexBy
```
