# Middle/middle+ level coding tasks

1. Binary tree sum

```javascript
/**
 * @param {object} tree
 * @return {number}
 * f({
    value: 2,
    left: {
      value: 1,
      left: null,
      right: null,
    },
    right: {
      value: 3,
      left: null,
      right: null,
    }
  }) -> 6
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const btree = {
    value: 2,
    left: {
      value: 1,
      left: null,
      right: null,
    },
    right: {
      value: 3,
      left: null,
      right: null,
    }
  };
  function findTreeSum(tree) {
    let result = tree.value;
    if (tree.left) result += findTreeSum(tree.left);
    if (tree.right) result += findTreeSum(tree.right);
    return result;
  };
  console.log(findTreeSum(btree));
</script>
<div>Complexity:</div>
<p><strong>??</strong></p>
</pre>
</details>

---

2. Code simple syntax analyser

```javascript
/**
* @param {string} s
* @return {boolean}
*...
* func("---(++++)----")) //  true
* func(""))  //  true
* func("before ( middle []) after ")) true
* func(")(")) false
* func("<( >)"))  false
* func("( [ <> () ] <> )")) true
* func(" (    [)")) false
*/
```
<details>
<summary>Solution 1</summary>
<pre>
<script>
function verify(s) {
  if (typeof s !== 'string') return false;
  const arr = [];
  const pairs = {
    open: ['(', '[', '{', '<',],
    close: [')', ']', '}', '>',]
  };
  for (let i = 0; i < s.length; i++) {
    const elem = s[i];
    if (pairs.open.includes(elem)) {
      arr.push(elem);
    } else if (pairs.close.includes(elem)) {
      //  key part of algorithm
      const firstPart = pairs.open[pairs.close.indexOf(elem)];
      if (arr[arr.length - 1] === firstPart) {
        arr.splice(-1, 1);
      //
      } else {
        arr.push(elem);
      }
    }
  }
  return arr.length === 0 ? true : false;
}
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

---

3. Find longest common preffix in the array of strings

```javascript
/**
* @param {string[]} strArr
* @return {string}
*
* func(["flower", "flow", "flight"])) -> 'fl'
* func(longestComPrfx([])) -> ''
* func(longestComPrfx(["flower"])) -> ''
* func(longestComPrfx(["", "", "", ""])) -> ''
* func(longestComPrfx(["flower", {}, null])) -> ''
* func([[], {}, "flower",  null])) -> ''
*/
```
<details>
<summary>Solution 1</summary>
<pre>
<script>
function longestComPrfx(strArr) {
  if (strArr.length < 2) return '';
  let commonPrefix = '';
  let candidateChar = '';
  let firstWord;
  //
  for (const word of strArr) {
    if (word && typeof word === 'string') {
      firstWord = word.toLowerCase();
      break;
    }
  }
  if (!firstWord) return '';
  //
  for (let i = 0; i < firstWord.length; i++) {
    candidateChar = firstWord[i] || '';  
    for (const word of strArr) {
      if (!word || typeof word !== 'string') continue;
      else {
        const loweredWord = word.toLowerCase();
        if (candidateChar !== loweredWord[i]) {
          return commonPrefix;
        }
      }
    }
    commonPrefix += candidateChar;
  }
  //
  if  (commonPrefix === firstWord) commonPrefix = '';
  return commonPrefix;
}
console.log(longestComPrfx(["flower", "flow", "flight"]));
console.log(longestComPrfx([]));
console.log(longestComPrfx(["flower"]));
console.log(longestComPrfx(["", "", "", ""]));
console.log(longestComPrfx(["flower", {}, null]));
console.log(longestComPrfx([[], {}, "flower",  null]));
</script>
<div>Complexity:</div>
<p><strong></strong></p>
</pre>
</details>

3. Simplest left binary search

```javascript
/**
* @param {number[]} a
* @param {number} x
* @return {boolean}
*...
* func([1,2,3,4,5], 4) -> 3
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
const arr = [1,2,3,4,5];
function lbSearch(a, x) {
  const N = a.length;
  let l = 0;
  let r = N - 1;
  while (l < r) {
    let m = Math.floor((l + r) / 2);
    if (a[m] < x) l = m + 1;
    else r = m;
  }
  return l;
}
console.log(lbSearch(arr, 4));
</script>
<div>Complexity:</div>
<p><strong>log(N)</strong></p>
</pre>
</details>

<details>
<summary>Solution 2</summary>
<pre>
<script>
function lbSearch(a, x) {
  const N = a.length;
  let l = 0;
  let r = N - 1;
  if (a[l] > x || a[r] < x) return - 1;
  while(true) {
    if (a[l] === x) return l;
    if (a[r] === x) return r;
    if (r - l <= 1) return -1;
    const m = Math.floor((l + r) / 2);
    if (a[m] < x) l = m + 1;
    else if (a[m] > x) r = m - 1
    else return m;
  }
}
console.log(lbSearch([1,2,3,4,5,6,7,8,9], 4)); //  3
</script>
<div>Complexity:</div>
<p><strong>log(N)</strong></p>
</pre>
</details>

---