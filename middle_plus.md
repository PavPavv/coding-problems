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