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
    for (let i = 0; i < arr.length; i++) {
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
<p><strong>O(n)</strong></p>
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
<p><strong>O(n)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>

</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---
