# Library of Utility Functions
## Recreation of the Underscore Library
```javascript
const arr = [1,2,3,4,5,6,7];
const car = [{make: "Ford", model: "Focus", color: "blue", tires: 4}, {miles: 6000, country: "USA"}, {tires: 4, tireBrand: "Firestone"},{interior: "leather", colorOfInterior: "black"}];

const {make, model, color, tires} = car[0];
const {miles,country} = car[1];
const {tireBrand} = car[2];
const {interior, colorOfInterior} = car[3];


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
  }
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
}
}
```
