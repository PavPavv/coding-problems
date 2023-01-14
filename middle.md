# Pre-middle/middle level coding tasks

1. Group anagram pairs

```javascript
/**
 * @param {string[]} str
 * @return {string[][]}
 * f(['ana', 'nan', 'pie', 'cort', 'iep']) -> [['ana', 'nan], ['pie', 'iep']]
*/
```

<details>
<summary>Bad solution</summary>
<pre>
<script>
  function groupAnagrams(arr) {
    const temp = [];
    const result = [];
    const set = new Set();
    for (let i = 0; i < arr.length; i++) {
      const sortedWord = arr[i].toLowerCase().split('').sort().join('');
      temp.push(sortedWord);
      set.add(sortedWord);
    }
    for (const word of set) {
      const group = [];
      for (let i = 0; i < temp.length; i++) {
        if (word === temp[i]) {
          group.push(arr[i]);
        }
      }
      result.push(group);
    }
    return result;
  }
  console.log(groupAnagrams(["eat","tea","tan","ate","nat","bat"]))  // [["ate","eat","tea"], ["nat","tan"], ["bat"]]
</script>
<div>Complexity:</div>
<p><strong>O(n^2) + O(k*n)</strong></p>
</pre>
</details>

<details>
<summary>Good solution</summary>
<pre>
<script>
function groupAnagrams(arr) {
  const map = new Map();
  for (let i = 0; i < arr.length; i++) {
    const sorted = arr[i].toLowerCase().split('').sort().join('').trim();
    const value = map.has(sorted) ? map.get(sorted) : [];
    value.push(arr[i]);
    map.set(sorted, value);
  }
  return [...map.values()];
}
 console.log(groupAnagrams(["eat","tea","tan","ate","nat","bat"])) // [["bat"],["nat","tan"],["ate","eat","tea"]]
</script>
<div>Complexity:</div>
<p><strong>O(n^2)</strong></p>
</pre>
</details>

<details>
<summary>Best solution </summary>
<pre>
<script>
function groupAnagrams(arr) {
  const hash = {};
  for (let i = 0; i < arr.length; i++) {
    const sorted = arr[i].toLowerCase().split('').sort().join('').trim();
    if (hash[sorted]) {
      hash[sorted].push(arr[i]);
    } else {
      hash[sorted] = [arr[i]];
    }
  }
  return Object.values(hash);
}
 console.log(groupAnagrams(["eat","tea","tan","ate","nat","bat"])) // [["bat"],["nat","tan"],["ate","eat","tea"]]
</script>
<div>Complexity:</div>
<p><strong>O(n^2)</strong></p>
</pre>
</details>

---

2. Find most popular character in the string.

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

3. Find first and second max numbers in the array.

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

4. Find min even number in the array.

```javascript
/**
 * @param {number[]} arr
 * @return {number}
 * f([10,-2,1,2,3,4,5]) -> -2
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function findMinEven(arr) {
    let flag = false;
    let result = arr[0];
    for (let i = 1; i < arr.length; i++) {
      if (arr[i] % 2 === 0 && (!flag || arr[i] < result)) {
        result = arr[i];
        flag = true;
      }
    }
    return result;
  }
  console.log(findMinEven([10,-2,1,2,3,4,5])) //  -2
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
  function findMinEven(array) {
    const sorted = array.sort((a,b) => a-b);
    for (let i = 0; i < sorted.length; i++) {
      if (sorted[i] % 2 === 0) {
        return sorted[i];
      }
    }
    return 0;
  }
  console.log(findMinEven([10,-2,1,2,3,4,5])) //  -2
</script>
<div>Complexity:</div>
<p><strong>O(n - k)</strong></p>
</pre>
</details>

<details>
<summary>Solution 3</summary>
<pre>
<script>
  function findMinEven(array) {
    let min = arr[0];
    for (let i = 0; i < arr.length; i++) {
      if (arr[i] % 2 === 0) {
        if (arr[i] < min) min = arr[i];
      }
    }
    return min;
  }
  console.log(findMinEven([10,-2,1,2,3,4,5])) //  -2
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

<details>
<summary>Solution 4</summary>
<pre>
<script>
  function findMinEven(arr) {
    return Math.min(...arr.filter((el) => el % 2 === 0));
  }
  console.log(findMinEven([10,-2,1,2,3,4,5])) //  -2
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

5. Create simple counter which will store value.

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

<details>
<summary>Solution 3 (ES5)</summary>
<pre>
<script>
  function counterF(num) {
    var counter = num || 0;
    return function() {
      return counter++;
    }
  }
  var count = counterF(100);
  count();
  count();
  count();
  console.log(count());
</script>
<div>Complexity:</div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---

6. Create string with char counter.

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
  const charCount = (str) => {
    const sortedStr = str.split('').sort().join('');
    const hashTable = {};
    let result = '';
    for (let i = 0; i < sortedStr.length; i++) {
      hashTable[sortedStr[i]] = hashTable[sortedStr[i]] ? hashTable[sortedStr[i]] + 1 : 1;
    }
    for (const char in hashTable) {
      result += `${char}${hashTable[char]}`
    }
    return result;
  }
  console.log(charCount('BBBAADDDDDECCCC'));  //  'A2B3C4D5E1'
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2 (ES6)</summary>
<pre>
<script>
  function charCount(str) {
    var sortedStr = str.split('').sort().join('');
    var hashTable = {};
    var result = '';
    for (let i = 0; i < sortedStr.length; i++) {
      hashTable[sortedStr[i]] = hashTable[sortedStr[i]] ? hashTable[sortedStr[i]] + 1 : 1;
    }
    for (const char in hashTable) {
      result += char + "" + hashTable[char];
    }
    return result;
  }
  console.log(charCount('BBBAADDDDDECCCC'));  //  'A2B3C4D5E1'
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

7. Fibonacci

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

8. Find out if a sum of two numbers in an array equals target number. All combinations must be **unique**.

```javascript
/**
 * @param {number[]} arr
 * @param {number} target
 * @return {number[]} 
 * func([1,2,3,4,5,6], 6) -> [[1,5], [2,4]];
 */
```

<details>
<summary>Solution 1 (bad)</summary>
<pre>
<script>
  function findAllUniqueSums(arr, target) {
    var result = [];
    for (var i = 0; i < arr.length; i++) {
      for (var j = 1; j < arr.length; j++) {
        if (arr[i]+arr[j] === target) {
          if (arr[i] > arr[j]) {
            result.push([arr[i],arr[j]]);
          }
        }
      }
    }
    return result;
}
console.log(findAllUniqueSums([3,5,300,1,7,4,-18,2,10,-5,23,11], 5));
</script>
<div>Complexity:</div>
<p><strong>O(n^2)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2 (good)</summary>
<pre>
<script>
  function findAllUniqueSums(arr, target) {
    var result = [];
    var obj = {};
    for (var i = 0; i < arr.length; i++) {
      obj[arr[i]] = arr[i];
    }
    console.log(obj)
    for (var num in obj) {
      var secondNum = target - num;
      if (obj[secondNum] && secondNum > num) {
        result.push([obj[secondNum],obj[num]]);
      }
    }
    return result;
  }
  console.log(findAllUniqueSums([3,5,300,1,7,4,-18,2,10,-5,23,11], 5));
</script>
<div>Complexity:</div>
<p><strong>O(N+K) (algoritm speed: O(N) + memory: O(K))</strong></p>
</pre>
</details>

---

9. Find out max index of two char in single string.

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

10. Compare two strings lexicographically

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 * f('banana', 'avocado') -> 'avocado'
*/
```

<details>
<summary>Solution 1 (long, custom, bad)</summary>
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
<summary>Solution 2 (long, custom)</summary>
<pre>
<script>
  function compare(a,b) {
    if (typeof a !== 'string' || typeof b !== 'string') {
      console.error('Both arguments must be a string');
      return;
    }
    if (!a) return b;
    if (!b) return a;
    for (let i = 0; i < a.toLowerCase().length; i++) {
      if (b[i]) {
        if (a[i].toLowerCase() < b[i].toLowerCase()) {
          return a;
        } else if (a[i].toLowerCase() > b[i].toLowerCase()) {
          return b;
        } else continue;
      } else {
        return b;
      }
    }
    return a.length === b.length ? a + " = " + b : a;
  }
  console.log(compare(-1, 30)); //  Type error
  console.log(compare('', '')); //  ''
  console.log(compare('', 'a'));  //  a
  console.log(compare('a', ''));  //  'a'
  console.log(compare('ab', 'a'));  //  'a'
  console.log(compare('banana', 'avocado'));  //  avocado
  console.log(compare('Banana', 'Avocado'));  //  Avocado
  console.log(compare('banana', 'Avocado'));  //  Avocado
  console.log(compare('ooooo', 'oo'));  //  oo
  console.log(compare('oo', 'oooooo')); //  oooooo
  console.log(compare('oz', 'oooooo')); //  oooooo
  console.log(compare('oooooo', 'oooooZ')); //oooooo
  console.log(compare('ooo', 'ooo')); // ooo = ooo
</script>
<div>Complexity:</div>
<p><strong>O(N)</strong></p>
</pre>
</details>

<details>
<summary>Solution 3 (short, native)</summary>
<pre>
<script>
function compare(str1, str2) {
  const result = str1.toString().localeCompare(str2.toString());
  return result ? str2 : str1;
}
console.log(compare(-1, 30)); //  Type error
console.log(compare('', '')); //  ''
console.log(compare('', 'a'));  //  a
console.log(compare('a', ''));  //  'a'
console.log(compare('banana', 'avocado'));  //  avocado
console.log(compare('Banana', 'Avocado'));  //  Avocado
console.log(compare('banana', 'Avocado'));  //  Avocado
console.log(compare('ooooo', 'oo'));  //  oo
console.log(compare('oo', 'oooooo')); //  oooooo
console.log(compare('oz', 'oooooo')); //  oooooo
console.log(compare('oooooo', 'oooooZ')); //oooooo
console.log(compare('ooo', 'ooo')); //ooo
</script>
<div>Complexity:</div>
<p><strong>O(1)</strong></p>
</pre>
</details>

<details>
<summary>Solution 4 (short, native)</summary>
<pre>
<script>
function compare(a,b) {
  if (typeof a !== 'string' || typeof b !== 'string') {
    return 'Both arguments must be a string'
  }
  if (!a) return b;
  if (!b) return a;
  var result = a.localeCompare(b);
  switch(result) {
    case 1:
      return b;
    case 0:
      return a + " = " + b;
    case -1:
      return a;
    default:
      return result;  
  }
}
console.log(compare(-1, 30)); //  Type error
console.log(compare('', '')); //  ''
console.log(compare('', 'a'));  //  a
console.log(compare('a', ''));  //  'a'
console.log(compare('banana', 'avocado'));  //  avocado
console.log(compare('Banana', 'Avocado'));  //  Avocado
console.log(compare('banana', 'Avocado'));  //  Avocado
console.log(compare('ooooo', 'oo'));  //  oo
console.log(compare('oo', 'oooooo')); //  oooooo
console.log(compare('oz', 'oooooo')); //  oooooo
console.log(compare('oooooo', 'oooooZ')); //ooooo0
console.log(compare('ooo', 'ooo')); //ooo
</script>
<div>Complexity:</div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---

11. Add new native method to the strings.

```javascript
/**
 * 'Hello'.repeating(3) -> 'Hello Hello Hello'
*/
```

<details>
<summary>Solution</summary>
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

12. Write myBind native method


<details>
<summary>Solution</summary>
<pre>
<script>
  Function.prototype.myBind = function(thisObj) {
    var self = this;
    return function() {
      self.call(thisObj);
    }
  };
  var test = someFn.myBind(someObj);
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

13. Write myForEach native method

<details>
<summary>Solution</summary>
<pre>
<script>
  Array.prototype.myForEach = function(cb) {
    for (var i = 0; i < this.length; i++) {
      cb(this[i],i,this);
    }
  };
  [1,2,3].myForEach(function(el) { console.log(el) })
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

14. Write reverse string method implemented in global string prototype

<details>
<summary>Solution</summary>
<pre>
<script>
String.prototype.reverse = function() {
  var result = '';
  var i = 0
  while (i < this.length) {
    i++;
    result += this[this.length - i];
  }
  return result;
}
console.log('test'.reverse()) //  'tset'
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

15. Write down 5 ways to create prototype in object in JS

<details>
<summary>Solution</summary>
<pre>
<script>
  'use strict';
  //  1 __proto__:
  const obj1 = {
    name: 'Jack',
  };
  const obj2 = {};
  obj2.__proto__ = obj1;
  console.log(obj2.name)  //  'Jack'
  // 2  Object.create:
  const obj1a = {
    name: 'Jack',
  };
  const obj2a = Object.create(obj1a);
  console.log(obj2a.name)  //  'Jack'
  // 3  setPrototypeOf
  const obj1b = {
    name: 'Jack',
  };
  const obj2b = {};
  Object.setPrototypeOf(obj2b, obj1b);
  console.log(obj2b.name)  //  'Jack'
  // 4  function-constructor with prototype (creating new object with given "this"):
  //  Animal
  function Animal(kind) {
    this.kind = kind || 'no kind';
  }
  Animal.prototype.getKind = function() {
    return this.kind;
  }
  Animal.prototype.setKind = function(k) {
    this.kind = k;
  }
  //  Dog
  function Dog(name) {
    this.name = name || 'no name';
  }
  // ES5 sort of inheritance
  Dog.prototype = new Animal;
  Dog.prototype.constructor = Animal;
  Dog.prototype.getName = function() {
    return this.name;
  }
  var myDog = new Dog('Jack');
  console.log(myDog.getName());
  myDog.setKind('shepherd');
  console.log(myDog.getKind());
  // ES6 sort of inheritance with classes syntax sugar:
  // Animal
  class Animal {
    constructor(kind) {
      this.kind = kind || 'no kind';
    }
    setKind(k) {
      this.kind = k;
    }
    getKind() {
      return this.kind;
    }
  }
  // Dog
  class Dog extends Animal {
    constructor(name) {
      super();
      this.name = name;
    }
    setName(n) {
      this.name = n;
    }
    getName() {
      return this.name;
    }
  }
  const myDoggy = new Dog('Jack');
  myDoggy.setKind('shepherd');
  console.log(myDoggy.getName());  //  'Jack'
  console.log(myDoggy.getKind());  //  'shepherd'
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

16. Write custom Object.create global method

<details>
<summary>Solution</summary>
<pre>
<script>
Object.prototype.myCreate = function(o) {
  function F() {}
  F.prototype = o;
  return new F();
}

</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

17. Find "black ship" in an array.

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
  function findBlackSheep(arr) {
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
  console.log(findBlackSheep([2,4,6,8,9,10,12]))
</script>
<div>Complexity:</div>
<p><strong>O(N)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
  function findBlackSheep(arr) {
    const binaryArr = arr.map(x => x % 2);
    const bArrSum = binaryArr.reduce((a,b) => a+b);
    const target = bArrSum > 1 ? 0 : 1;
    return arr[binaryArr.indexOf(target)];
  };
  console.log(findBlackSheep([2,4,6,8,9,10,12]))
</script>
<div>Complexity: </div>
<p><strong>O(N)</strong></p>
</pre>
</details>

---

18. Find list of shortest strings in the array

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
<p><strong>O(N)</strong></p>
</pre>
</details>

---

19. Create expression, like: five(plus(seven(minus(three())))) which returns 9

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

---

20. Write a function which will return accumulated amount of seconds since previous tick

```javascript
/**
* @param {number}
* @return {void}
*...
* func(1) -> 1...,2......,3.........,4............,5...............,6..................,7.....................,8........................, ...10...
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function periodOutput(interval) {
    let counter = interval;
    const tick = 1000 * counter;
    setTimeout(() => {
      if (counter <= 10) {
        console.log(counter);
        counter++;
        periodOutput(counter);
      }
      return;
    }, tick);
  }
  console.log(periodOutput(1));
</script>
<div>Complexity: </div>
<p><strong>O(1)</strong></p>
</pre>
</details>

---
