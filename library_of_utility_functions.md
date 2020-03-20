```javascript
#Library of Utility Functions
const arr = [1,2,3,4,5,6,7];

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
}
```