# Top Coding Questions
Top interview coding questions and my solutions

1. Find the missing number in the array ([solution](https://codesandbox.io/s/find-missing-number-in-an-array-dsdrc?file=/src/index.js))
```javascript
// time complexity is O(n)
const findMissingNumber = (arr) => {
  const length = arr.length;
  let sum = 0;

  for (let i = 1; i <= length + 1; i++) {
    sum += i;
  }

  for (let i = 0; i < length; i++) {
    sum -= arr[i];
  }

  console.log(`Missing number is ${sum}`);
};

findMissingNumber([3, 7, 6, 2, 8, 4, 5]);
```

2. Determine if the sum of two integers is equal to the given value ([solution](https://codesandbox.io/s/find-sum-of-two-cpl9f))
```javascript
// time complexity O(n)
// space complexity O(n)
function findSumOfTwo(nums, sum) {
  if (nums.length > 0 || sum === 0) {
    let dict = {};
    for (let i = 0; i < nums.length; i++) {
      dict[nums[i]] = sum - nums[i];
    }

    for (let key in dict) {
      if (nums.includes(Number(key)) && nums.includes(dict[key])) {
        return true;
      }
    }
  }
  return false;
}

console.log(findSumOfTwo([5, 2, 8, 4], 13));
```
