# Junior level coding tasks

1. Find **first** left target in the array.
```javascript
/**
 * @param {number}
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
</pre>
</details>