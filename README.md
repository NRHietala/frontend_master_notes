# frontend_master_notes
## Reduce Method 

```javascript
const arr = [1,2,3,4,5,6,7];

const reduce = (array, initialValue, f) => {
  let result = initialValue;
  for (const ele of array) {
    result = f(ele, result);
  }
  return result;
}

const map = (array, f) => {
  return reduce(array, [], function(ele, result) {
    result.push(f(ele));
    return result;
  })
}

const filter = (array, p) => {
  return reduce(array, [], function(ele, result) {
    if (p(ele)) {
      result.push(ele);
    }
    return result;
  })
}

reduce(arr, 1, function(ele, result) {
  return ele * result;
})
```
