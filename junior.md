# Junior level coding tasks

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
<p><strong>O(n)</strong></p>
</pre>
</details>

8. Transform number into number consisting of square of each number. Number must be more than 9;
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
<p><strong>O(n)</strong></p>
</pre>
</details>

9. Replace character from the string
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
const removeChar = (str) => {
  return str.replace(/#/gi,'');
};
console.log(removeChar('Hell#o!'));
</script>
<p><strong>O(n)</strong></p>
</pre>
</details>