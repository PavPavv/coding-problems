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
<p>O(n)</p>
</pre>
</details>

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
<p>O(n)</p>
</pre>
</details>

3. Find out is a string palindrome or not.
```javascript
/**
 * @param {string} str
 * @return {boolean}
 * f('ana') -> true
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function isPalindrome = (str) => {
    str = str.toLowerCase();
    return str === str.split("").reverse().join("");
  };
  console.log(isPalindrome('ana')); // true
</script>
<p>O(n)</p>
</pre>
</details>

4. Find elements of array having target length.
```javascript
/**
 * @param {string[]} arr
 * @param {number} target
 * @return {string[]}
 * f(["Mark", "John", "Anna", "Maria"]) -> ["Mark", "John", "Anna"]
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  function findByParam(arr, target) {
    return arr.filter((elem) => elem.length === target);
  }
  console.log(findByParam(["Mark", "John", "Anna", "Maria"]));
</script>
<p>O(n)</p>
</pre>
</details>