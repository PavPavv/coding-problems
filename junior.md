# Junior level coding tasks

---

1. Find first **left** target in the array.

```javascript
/**
 * @param {number} array
 * @param {number} target
 * @return {number}
 * f([1,2,3,1,2,3],3) -> 2
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function findFirstLeft(array, target) {
    for (let i = 0; i < array.length; i++) {
      if (array[i] === target) return i;
    }
    return -1;
  }
  console.log(findFirstLeft([1,2,3,1,2,3], 3));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

2. Find first **right** target in the array.

```javascript
/**
 * @param {number} array
 * @param {number} target
 * @return {number} 
 * f([1,2,3,1,2,3],3) -> 5
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function findFirstRight(array, target) {
    let counter = -1;
    for (let i = 0; i < array.length; i++) {
      if (array[i] === target) counter = i;
    }
    return counter;
  }
  console.log(findFirstRight([1,2,3,1,2,3], 3));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

3. Find out is a string palindrome or not.

```javascript
/**
 * @param {string} str
 * @return {boolean}
 * f('ana') -> true
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function isPalindrome = (str) => {
    str = str.toLowerCase();
    return str === str.split("").reverse().join("");
  };
  console.log(isPalindrome('ana')); // true
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

4. Find elements of array having target's length.

```javascript
/**
 * @param {string[]} arr
 * @param {number} target
 * @return {string[]}
 * f(["Mark", "John", "Anna", "Maria"]) -> ["Mark", "John", "Anna"]
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function findByParam(arr, target) {
    return arr.filter((elem) => elem.length === target);
  }
  console.log(findByParam(["Mark", "John", "Anna", "Maria"]));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

5. Count amount of vowels in the word.

```javascript
/**
 * @param {string} word
 * @return {number}
 * f('wolf') -> 1
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function vowelsCounter(word) {
    const VOWELS = ['a','e','i','o','u'];
    let counter = 0;
    for (let i = 0; i < word.length; i++) {
      if (VOWELS.includes(word[i])) counter++;
    }
    return counter;
  }
  console.log(vowelsCounter('wolf'));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
  function vowelsCounter(word) {
    const matched = word.match(/[aeiou]/gi);
    return matched ? matched.length : 0;
  }
  console.log(vowelsCounter('wolf'));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

6. Find sum of the range in between **two** numbers.

```javascript
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 * f(1,5) -> 15
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function getSumOfTwoNumsRange(a,b) {
    const start = a > b ? b : a;
    const end = a > b ? a : b;
    let counter = 0;
    for (let i = start; i <= end; i++) {
      counter += i;
    }
    return counter;
  }
  console.log(getSumOfTwoNumsRange(1,5));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

7. Find middle character of the string if the string length is even or first char right after the middle if the string length is odd.

```javascript
/**
 * @param {string} str
 * @return {string}
 * f('testing') -> 't'
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function findMiddle(str) {
    const isEven = str.length % 2 === 0 ? true : false;
    const oddMiddle = str[(str.length - 1) / 2];
    const evenMiddle = str[str.length / 2];
    return isEven ? evenMiddle : oddMiddle;
  }
  console.log(findMiddle('test'));
  console.log(findMiddle('testing'));
</script>
<div>Complexity:</div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---

8. Transform number into number consisting of square of each number. Input number must be more than 9.

```javascript
/**
 * @param {number} num
 * @return {number}
 * f(25) -> 425 (4+25)
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
const squareDigits = (num) => {
  return +num
    .toString()
    .split('')
    .map(n => n * n)
    .join('')
};
console.log(squareDigits(25));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

9. Replace character from the string.

```javascript
/**
 * @param {string} str
 * @return {string}
 * f('Hell#o!') -> 'Hello!'
*/
```

<details>
<summary>Solution</summary>
<pre>
<script>
const removeChar = (str, target) => {
  const targetRegex = new RegExp(target, 'gi');
  return str.replace(targetRegex,'');
};
console.log(removeChar('Hell#o!', '#'));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

10. Find out if there is element in the array that is the same as the previous one

```javascript
/**
 * @param {number[]} arr
 * @return {boolean}
 * f([2,4,5,1,3,3,7,8,9,10,300]) -> true
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function isRepeat(arr) {
    if (Array.isArray(arr)) {
      for (let i = 1; i < arr.length; i++) {
        const prev = arr[i - 1];
        if (prev === arr[i]) return true;
      }
    }
    return false;
  }
  console.log(isRepeat(''));
  console.log(isRepeat([2,4,5,1,3,45,7,8,9,10,300]));
  console.log(isRepeat([1,1,2,4,5,1,3,3,7,8,9,10,300]));
  console.log(isRepeat([2,4,5,1,3,3,7,8,9,10,300]));
</script>
<div>Complexity:</div>
<p><strong>O(n - 1)</strong></p>
</pre>
</details>

---

11. Find one duplicated sequence

```javascript
/**
 * @param {number[]} arr
 * @return {boolean}
 * f([1,2,3,4,5,6,7,8,3,9]) -> [3,3]
*/
```

<details>
<summary>Bad solution</summary>
<pre>
<script>
  function findRepeat(arr) {
    var result = [];
    for (var i = 0; i < arr.length; i++) {
      for (var j = 0; j < arr.length; j++) {
        if (arr[i] === arr[j] && i !== j) {
          result.push(arr[i]);
        }
      }
    }
    return result;
  }
  console.log(findRepeat([1,2,3,4,5,6,7,8,3,9]));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

<details>
<summary>Good solution</summary>
<pre>
<script>
  function findRepeat(arr) {
    const result = [];
    const cache = {};
    for (let i = 0; i < arr.length; i++) {
      obj[arr[i]] = i;
    }
    for (const n of arr) {
      if (arr.indexOf(n) !== obj[n]) {
        result.push(n)
      }
    }
    return result;
  }
  console.log(findRepeat([1,2,3,4,5,6,7,8,3,9]));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

---

12. Find ALL duplicated sequence and return them as arrays

```javascript
/**
 * @param {number[]} arr
 * @return {boolean}
 * f([1,2,3,4,5,6,7,8,3,9]) -> [3,3]
*/
```

<details>
<summary>Good solution</summary>
<pre>
<script>
  function findRepeats(arr) {
    const result = [];
    const cache = {};
    for (let i = 0; i < arr.length; i++) {
      cache[arr[i]] = cache[arr[i]] ? cache[arr[i]] + 1 : 1;
    }
    for (const n in cache) {
      if (cache[n] > 1) {
        const a = new Array(cache[n]).fill(n);
        result.push(a);
      }
    }
    return result;
  }
  console.log(findRepeats([1,2,3,4,5,3,6,7,5,8,9,5])); // [[3,3], [5,5,5]]
  </script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

13. Name proper sequence of the event loop calls.

<details>
<summary>Solution 1</summary>
<pre>
<script>
  new  Promise(function(resolve, reject) {
    return new Promise(function(resolve, reject) {
      return resolve(setTimeout(function() {
        console.log(1)
      }, 1000));
    })
  });
  new  Promise(function(resolve, reject) {
    return resolve(console.log(2));
  });
  console.log(3);
  var promise = new Promise(function(resolve, reject) {
    return reject(console.log(4));
  });
  setTimeout(function() {
    console.log(5);
  },0)
  function main() {
    console.log(6);
  }
  promise.then(function(success) {
    console.log(7);
  }, function (error) {
    console.log(8);
  });
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

14. Find a number of coincidences in the array from half-interval for a number param.

```javascript
/**
 * @param {number[]} arr
 * @param {number} l
 * @param {number} r
 * @param {number} target
 * @return {number}
 * f([0,0,0,0,1,2,3,4,5,6,0,], 1, 5, 0) -> 3
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const nums = [0,0,0,0,1,2,3,4,5,6,0,0];
  function halfIntervalTargetCounter(arr, l ,r, target) {
    let counter = 0;
    for (let i = l; i < r; i ++) {
      if (arr[i] === target) counter++;
    }
    return counter;
  }
  console.log(halfIntervalTargetCounter(nums, 1, 5, 0));
</script>
<div>Complexity:</div>
<p><strong>O(N*M)</strong></p>
</pre>
</details>

---

15. Find out if two numbers in the array have target sum.

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 * f([2,3,5,1,6,7,8,10,100], 5) -> true
 * f([2,3,5,1,6,7,8,10,100], 1000) -> false
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const nums = [2,3,5,1,6,7,8,10,100];
  function isHaveSum(arr, target) {
    for (let i = 0; i < arr.length; i++) {
      for (let j = 0; j < arr.length; j++) {
        if (arr[i] + arr[j] === target) return true;
      }
    }
    return false;
  }
  console.log(isHaveSum(nums, 5));
  console.log(isHaveSum(nums, 1000));
</script>
<div>Complexity:</div>
<p><strong>O(N^2)</strong></p>
</pre>
</details>

---

16. Convert all the params into a string with separator.

```javascript
/**
* @param {string}
* @param {number}
* @param {number}
* ...
* @return {string}
*...
* func('!', 4, -10, 34, 0) -> '!4!-10!34!0'
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function withSeparator(...rest) {
    const [separator, ...values] = rest;
    return separator + values.join(separator);
  };
  console.log(withSeparator('!', 4, -10, 34, 0));
</script>
<div>Complexity: </div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---

---

17. Find out if object is empty.

```javascript
/**
* @param {object}
* @return {boolean}
*...
* func({}) -> true
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function isEmptyObj(obj) {
    return Object.keys(obj).length > 0 ? false : true;
  }
  console.log(isEmptyObj({}));
  console.log(isEmptyObj({a: 'test'}));
</script>
<div>Complexity: </div>
<p><strong>O(N)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
  function isEmptyObj(obj) {
    for (const key in obj) {
      return false;
    }
    return true;
  }
  console.log(isEmptyObj({}));
  console.log(isEmptyObj({a: 'test'}));
</script>
<div>Complexity: </div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---
18. Find max value in the array

```javascript
/**
* @param {number[]}
* @return {number}
*...
* func([3,5,2,1,3,7,66,8,9,4,100,45]) -> 100
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function findMax(arr) {
    let max = 0;
    for (let i= 0; i < arr.length; i++) {
      if (arr[i] > max) {
        max = arr[i];
      }
    }
    return max;
  }
  console.log(findMax([3,5,2,1,3,7,66,8,9,4,100,45]));
</script>
<div>Complexity: </div>
<p><strong>O(N)</strong></p>
</pre>
</details>

---

19. Find shortest string in the array

```javascript
/**
* @param {string[]}
* @return {string}
*...
* func(['ab', 'a', 'abc']) -> a
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const wordsArr = ['kryliaSovetov', 'zenit', 'spartak'];
  function getShortestStrFromArr(arr) {
    let min = arr[0];
    for (let i = 1; i < arr.length; i++) {
      if (arr[i].length < min.length) {
        min = arr[i];
      }
    }
    return min;
  }
  console.log(getShortestStrFromArr(wordsArr)); //  zenit
</script>
<div>Complexity: </div>
<p><strong>O(N-1)</strong></p>
</pre>
</details>

---

20. Write a function which will return amount of second passed by since its start 'till 10sec

```javascript
/**
* @param {number}
* @return {void}
*...
* func(1) -> 1...,2...,3...,4...,5...,6...,7...,8...,9...,10....
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function periodOutput(interval) {
    let counter = 1;
    setInterval(() => {
      if (counter <= 10) {
        console.log(counter);
        counter++;
      }
      return;
    }, 1000 * interval);
  }
  console.log(periodOutput(1));
</script>
<div>Complexity: </div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---

21. Write a function which will return arrays of pairs of numbers if its sum equals target number or empty arrays conversely.

```javascript
/**
 * @param {number[]} arr
 * @param {number} target
 * @return {number[]} 
 * func([1,2,3,4,5,6], 6) -> [[1,5], [2,4]];
 */
```

<details>
<summary>Solution 1 (naive dirty solution)</summary>
<pre>
<script>
function findSum(arr, target) {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
      if (arr[i] + arr[j] === target) {
        const pair = [arr[i], arr[j]];
        result.push(pair);
      }
    }
  }
  return result;
}
</script>
<div>Complexity: </div>
<p><strong>O(N^2)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
function findSum(arr, target) {
  const result = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = 0; j < arr.length; j++) {
      //  more complex check
      if (arr[i] + arr[j] === target && arr[i] !== arr[j] && arr[i] < arr[j]) {
        const pair = [arr[i], arr[j]];
        result.push(pair);
      }
    }
  }
  return result;
}
</script>
<div>Complexity: </div>
<p><strong>O(N^2) (algoritm speed: O(N^2) + memory: O(1))</strong></p>
</pre>
</details>

---
