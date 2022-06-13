# Middle/middle+ level coding tasks

1. Binary tree sum

```javascript
/**
 * @param {object} tree
 * @return {number}
 * f({...}) -> 6
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
