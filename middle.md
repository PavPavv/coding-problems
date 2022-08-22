# Pre-middle/middle level coding tasks

1. Find most popular character in the string.

```javascript
/**
 * @param {string} str
 * @return {number}
 * f('ababa') -> 'a'
*/
```
<details>
<summary>Bad solution</summary>
<pre>
<script>
  function popularSymbol(str) {
    let newStr = str.replace(/\s/g, '');
    let ans = '';
    let counter = 0;
    for (let i = 0; i < newStr.length; i++) {
      let currentCounter = 0;
      for (let j = 0; j < newStr.length; j++) {
        if (str[i] === str[j]) {
          currentCounter += 1;
        }
      }
      if (currentCounter > counter) {
        ans = str[i];
        counter = currentCounter;
      }
    }
    return ans;
  }
  console.log(popularSymbolObj('ababa')) // 'a'
</script>
<div>Complexity:</div>
<p><strong>O(n^2)</strong></p>
</pre>
</details>

<details>
<summary>Good solution</summary>
<pre>
<script>
  function popularSymbolObj(str) {
    let newStr = str.replace(/\s/g, '');
    let ans = '';
    let counter = 0;
    let obj = {};
    for (let i = 0; i < newStr.length; i++) {
      obj[newStr[i]] = obj[newStr[i]] ? obj[newStr[i]] + 1 : 1;
    }
    for (let key in obj) {
      if (obj[key] > counter) {
        counter = obj[key];
        ans = key;
      }
    }
    return ans;
  }
  console.log(popularSymbolObj('ababa')) // 'a'
</script>
<div>Complexity:</div>
<p><strong>O(n + k) k< n => O(n)</strong></p>
</pre>
</details>

---

2. Find first and second max numbers in the array.

```javascript
/**
 * @param {number[]} arr
 * @return {number[]}
 * f([10,-2,1,2,3,4,5]) -> [10,5]
*/
```
<details>
<summary>Solution</summary>
<pre>
<script>
  function findTwoMax(arr) {
    let max1 = Math.max(arr[0], arr[1]);
    let max2 = Math.min(arr[0], arr[1]);
    for (let i = 2; i < arr.length; i++) {
      if (arr[i] > max1) {
        max2 = max1;
        max1 = arr[i];
      } else if (arr[i] > max2) {
        max2 = arr[i];
      }
    }
    return [max1, max2];
  }
  console.log(findTwoMax([10,-2,1,2,3,4,5])); //  [10,5]
</script>
<div>Complexity:</div>
<p><strong>O(n - 2)</strong></p>
</pre>
</details>

---

3. Find min even number in the array.

```javascript
/**
 * @param {number[]} arr
 * @return {number}
 * f([10,-2,1,2,3,4,5]) -> 2
*/
```
<details>
<summary>Solution</summary>
<pre>
<script>
  function findMinEven(arr) {
    let flag = false;
    let result = 0;
    for (let i = 1; i < arr.length; i++) {
      if (arr[i] % 2 === 0 && (!flag || arr[i] < result)) {
        result = arr[i];
        flag = true;
      }
    }
    return result;
  }
  console.log(findMinEven([10,-2,1,2,3,4,5])) //  2
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

4. Create simple counter which will store value.

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const counter = (num) => {
    let count = num || 0;
    return () => count++;
  };
  const count1 = counter(100);
  count1();
  count1();
  count1();
  console.log(count1());  //  103
</script>
<div>Complexity:</div>
<p><strong>O(1)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2 (with IIFE)</summary>
<pre>
<script>
  const counter = (function () {
    let counter = 0;
    return function () {
      return counter++;
    }
  })();
  counter();
  counter();
  counter();
  console.log(counter())  //  3
</script>
<div>Complexity:</div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---

5. Create string with char counter.

```javascript
/**
 * @param {string} str
 * @return {string}
 * f('AABBBCCCCDDDDDE') -> 'A2B3C4D5E1'
*/
```
<details>
<summary>Solution 1</summary>
<pre>
<script>
  function charCount(str) {
    const spacelessStr = str.replaceAll(/\s/g, '');
    const obj = {};
    let result = '';
    for (let i = 0; i < spacelessStr.length; i++ ) {
      obj[spacelessStr[i]] = obj[spacelessStr[i]] ? obj[spacelessStr[i]] + 1 : 1;
    }
    for (const char in obj) {
      result += `${char}${obj[char]}`;
    }
    return result;
  }
  console.log(charCount('AABBBCCCCDDDDDE'));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

6. Fibonacci

```javascript
/**
 * @param {number} num
 * @return {number}
 * f(9) -> 34
*/
```
<details>
<summary>Solution 1 (recursive)</summary>
<pre>
<script>
  function fib(num) {
    if (num < 2) return num;
    return fib(num - 1) + fib(num - 2);
  };
  console.log(fib(9));  //  34
</script>
<div>Complexity:</div>
<p><strong>O(2^n)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2 (without recursion)</summary>
<pre>
<script>
  function fib(num) {
    const result = [0, 1];
    for (let i = 2; i <= num; i++) {
      let prev1 = result[i - 1];
      let prev2 = result[i - 2];
      result.push(prev1 + prev2);
    }
    return result[num];
  };
console.log(fib(9));  //  34
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

7. Find out if two numbers in the array have target sum. All combinations must be **unique**.

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 * f([2,3,5,1,6,7,4,8,10,100,4,300,24,1], 5) -> [[2,3], [1,4], [4,1]]
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const nums = [2,3,5,1,6,7,4,8,10,100,4,300,24,1];
  function getSumPairs(arr, target) {
    const set = new Set();
    const result = [];
    for (let i = 0; i < arr.length; i++) {
      set.add(arr[i]);
    }
    for (const num of set) {
      const secondNum = target - num;
      if (set.has(secondNum)) {
        if (secondNum > num) {
          result.push([num, secondNum]);
        }
      }
    }
    return result;
  }
  console.log(getSumPairs(nums, 5));
</script>
<div>Complexity:</div>
<p><strong>O(N+K)??</strong></p>
</pre>
</details>

---

8. Find out max index of two char in single string.

```javascript
/**
 * @param {string} str
 * @param {string} a
 * @param {string} b
 * @return {number}
 * f('abbaao', 'a', 'b') -> 4
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function getLatestCharIdx(str, a, b) {
    if (str) {
      if (!a && !b) return -1;
      return Math.max(
        a ? str.lastIndexOf(a) : -1,
        b ? str.lastIndexOf(b) : -1
      );
    }
    return -1;
  }
  console.log(getLatestCharIdx('google', 'g', 'o'));  //  3
  console.log(getLatestCharIdx('aba', 'a', 'b'));  //  2
  console.log(getLatestCharIdx('', 'g', 'o'));   //  -1
  console.log(getLatestCharIdx('google', 'x', 'o')); //  2
  console.log(getLatestCharIdx('aba', '', '')); //  -1
  console.log(getLatestCharIdx('aba', '', 'b')) //  1
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
  function getLatestCharIdx(s, a, b) {
    if (typeof s !== 'string') return -1;
    if (s) {
      if (a && b) {
        let a_result = 0;
        let b_result = 0;
        for (let i = 0; i < s.length; i++) {
          if (s[i] === a) a_result = i;
          if (s[i] === b) b_result = i;
        }
        return a_result > b_result ? a_result : b_result;
      }
    }
    return -1;
  };
  console.log(getLatestCharIdx('aba', 'a', 'b'));  //  2
  console.log(getLatestCharIdx('', 'g', 'o'));   //  -1
  console.log(getLatestCharIdx('google', 'x', 'o')); //  2
  console.log(getLatestCharIdx('aba', '', '')); //  -1
  console.log(getLatestCharIdx('aba', '', 'b')) //  1
</script>
<div>Complexity: </div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

9. Compare two strings lexicographically

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 * f('banana', 'avocado') -> 'avocado'
*/
```

<details>
<summary>Solution 1 (long, custom)</summary>
<pre>
<script>
  function compare(a, b) {
    if (typeof a !== 'string' || typeof b !== 'string') {
      return 'Type error';
    }
    if (!a && !b) return 'The strings are empty';
    if (!a) return b;
    if (!b) return a;
    const loweredA = a.toLowerCase();
    const loweredB = b.toLowerCase();
    for (let i = 0; i < loweredA.length; i++) {
      const charCodeA = loweredA[i] ? loweredA[i].charCodeAt() : -1;
      const charCodeB = loweredB[i] ? loweredB[i].charCodeAt() : -1;
        if (charCodeA < charCodeB) return a;
      if (charCodeA > charCodeB) return b;
      if (charCodeA === charCodeB) {
        if (loweredA.length > loweredB.length) {
          if (loweredB[loweredB.length - 1] === loweredA[i]) {
            return b;
          } else {
            continue;
          };
        } else if (loweredA.length < loweredB.length) {
          if (loweredA[loweredA.length - 1] === loweredB[i]) {
            return a;
          } else {
            continue;
          };
        } else {
          return a;
        }
      }
    }
  };
  console.log(compare(-1, 30)); //  Type error
  console.log(compare('', '')); // The strings are empty 
  console.log(compare('', 'a'));  //  a
  console.log(compare('a', ''));  //  a
  console.log(compare('banana', 'avocado'));  //  avocado
  console.log(compare('Banana', 'Avocado'));  //  Avocado
  console.log(compare('banana', 'Avocado'));  //  Avocado
  console.log(compare('ooooo', 'oo'));  //  oo
  console.log(compare('oo', 'oooooo')); //  oo
  console.log(compare('oz', 'oooooo')); //  oooooo
  console.log(compare('oooooo', 'oooooZ')); //  oooooo
  console.log(compare('ooo', 'ooo')); //  ooo
</script>
<div>Complexity:</div>
<p><strong>O(N)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2 (short, native)</summary>
<pre>
<script>
function compare(str1, str2) {
  const result = str1.toString().localeCompare(str2.toString());
  return result ? str2 : str1;
}
console.log(compare(-1, 30)); //  30
console.log(compare('', '')); //  ''
console.log(compare('', 'a'));  //  a
console.log(compare('a', ''));  //  ''
console.log(compare('banana', 'avocado'));  //  avocado
console.log(compare('Banana', 'Avocado'));  //  avocado
console.log(compare('banana', 'Avocado'));  //  avocado
console.log(compare('ooooo', 'oo'));  //  oo
console.log(compare('oo', 'oooooo')); //  oooooo
console.log(compare('oz', 'oooooo')); //  oooooo
console.log(compare('oooooo', 'oooooZ')); //oooooZ
console.log(compare('ooo', 'ooo')); //ooo
</script>
<div>Complexity:</div>
<p><strong>??</strong></p>
</pre>
</details>

---

10. Add new native method to the strings.

```javascript
/**
 * 'Hello'.repeating(3) -> 'Hello Hello Hello'
*/
```

<details>
<summary>Solution 2 (short, native)</summary>
<pre>
<script>
  String.prototype.repeating = function(num) {
    return new Array(num).fill(this).join(" ");
  };
  'Hello'.repeating(3);
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

11. Find "black ship" in an array.

```javascript
/**
 * @param {number[]} arr
 * @return {number}
 * f([2,4,6,8,9,10,12]) -> 9
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function findBlackShip(arr) {
    let oddCounter = 0;
    let evenCounter = 0;
    let lastOdd = 0
    let lastEven = 0;
    for (let i = 0; i < arr.length; i++) {
      if (arr[i] % 2 === 0) {
        evenCounter++;
        lastEven = arr[i];
      } else {
        oddCounter++;
        lastOdd = arr[i];
      }
    }
    if (evenCounter + oddCounter > 3) {
      if (oddCounter > 1) return lastEven;
      else return lastOdd;
    } else return -1;
  };
</script>
<div>Complexity:</div>
<p><strong>O(N)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
  function findBlackShip(arr) {
    const binaryArr = arr.map(x => x % 2);
    const bArrSum = binaryArr.reduce((a,b) => a+b);
    const target = bArrSum > 1 ? 0 : 1;
    return arr[binaryArr.indexOf(target)];
  };
  console.log(findBlackShip([2,4,6,8,9,10,12]))
</script>
<div>Complexity: </div>
<p><strong>O(N)</strong></p>
</pre>
</details>

---

12. Find list of shortest strings in the array

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
  const wordsArr = ['mu', 'kryliaSovetov', 'zenit', 'spartak', 'sochi', 'mc'];
  function getShortestStrFromArr(arr) {
    let min = arr[0];
    const result = [];
    for (const word of arr) {
      if (word.length < min.length) {
        min = word;
      }
    }
    for (const word of arr) {
      if (word.length === min.length) {
        result.push(word);
      }
    }
    return result.length > 0 ? result : min;
  }
  console.log(getShortestStrFromArr(wordsArr)); //  ['mu', 'mc']
</script>
<div>Complexity: </div>
<p><strong>O(N-1)</strong></p>
</pre>
</details>

---

13. Create expression, like: five(plus(seven(minus(three())))) which returns 9

<details>
<summary>Solution 1</summary>
<pre>
<script>
function plus(x) {
  return function(y) {
    return y + x;
  }
}
function minus(x) {
  return function(y) {
    return y - x;
  }
}
//  key of the algorithm
function expression(number, operation) {
  if (!operation) return number;
  return operation(number);
}
//
function three(operation) {
  return expression(3, operation);
}
function five(operation) {
  return expression(5, operation);
}
function seven(operation) {
  return expression(7, operation);
}
console.log(five(plus(seven(minus(three())))));
</script>
<div>Complexity: </div>
<p><strong></strong></p>
</pre>
</details>