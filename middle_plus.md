# Middle/middle+ level coding tasks

1. Binary tree to array

```javascript
/**
 * @param {object} tree
 * @return {number[]}
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
  const tree = {
    value: 1,
    children: [
      {
        value: 2,
        children: [
          {
            value: 3,
          },
        ],
      },
      {
        value: 4,
        children: [
          {
            value: 5,
          },
          {
            value: 6,
          },
        ]
      },
    ],
  };
  function getTreeValues(t) {
    var stack = [t];
    var result = [];
    while (stack.length > 0) {
      var node = stack.pop();
      if (node.value !== undefined) {
        result.push(node.value);
      }
      if (node.children?.length) {
        stack.push(...node.children);
      }
    }
    return result;
  }
  console.log(getTreeValues(tree));
</script>
<div>Complexity:</div>
<p><strong>O(n)</strong></p>
</pre>
</details>

---

2. Binary tree sum

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

3. Code simple syntax analyser

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

4. Find longest common preffix in the array of strings

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

5. Simplest left binary search

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

6. Write your own parseInt

```javascript
/**
  @param {string} str
  @return {number}
  func('123') -> 123
*/
```

<details>
<summary>Solution 1</summary>
<pre>
<script>
function myParseInt(str) {
  let int = 0;
  for (let i = 0; i < str.length; i++) {
    const asciiCode = str[i].charCodeAt();
    const digit = String.fromCharCode(asciiCode);
    int += digit;
  }
  return int * 10 / 10;
}
console.log(myParseInt('123')); //  123
console.log(myParseInt('20458')); //  20458
</script>
<div>Complexity:</div>
<p><strong>log(N)</strong></p>
</pre>
</details>

---

7. Find out if a sum of two numbers in a **sorted** array equals target number. All combinations must be **unique**.

```javascript
/**
 * @param {number[]} arr
 * @param {number} target
 * @return {number[]}
 * func([1,2,3,4,5,6], 6) -> [[1,5], [2,4]];
 */
```

<details>
<summary>Solution 1 (with binary search)</summary>
<pre>
<script>
  function findSum(arr, target) {
    const result = [];
    for (let i = 0; i < arr.length; i++) {
      const secondNum = target - arr[i];
      let l = i + 1;
      let r = arr.length - 1;
      while (l <= r) {
        let m = Math.ceil(l + (r - l) / 2);
        if (arr[m] === secondNum) {
          const pair = [arr[i], arr[m]];
          result.push(pair);
        }
        if (secondNum < arr[m]) {
          r = m - 1;
        } else {
          l = m + 1;
        }
      }
    }
    return result;
  }
</script>
<div>Complexity:</div>
<p><strong>log(N)</strong></p>
</pre>
</details>

---

8. Write a function which will return arrays of number tuples consisting of two number which sum is equal to target. Or closest result.

```javascript
/**
 * @param {number[]} arr
 * @param {number} target
 * @return {number[]}
 * func([1,2,3,4,5,6], 6) -> [[1,5], [2,4]];
 */
```

<details>
<summary>Solution</summary>
<pre>
<script>
  function findSum(arr, target) {
    const result = [];
    for (let i = 0; i < arr.length; i++) {
      let l = 0;
      let r = arr.length - 1;
      let pair = [arr[l], arr[r]];
      while (l < r) {
        const sum = arr[l] + arr[r];
        if (sum === target) {
          pair = [arr[l], arr[r]];
          return pair;
        }
        if (sum < target) {
          l++;  
        } else {
          r--;
        }
      }
    }
    return result;
  }
</script>
<div>Complexity:</div>
<p><strong>log(N)</strong></p>
</pre>
</details>

---

9. Write a function which splits text into a small messages. 1 sms must be smaller than 140 characters and should end with ' k/n' suffix, where n - the whole amount of messages and k - current number of message. No punctuation and symbols except latin letter and spaces are allowed. sms can't be divided in the middle of a word. No words wrapping.

```javascript
/***
 * @param {string} text
 * @return {string[]}
 * func('some super... long string') -> ['message 1/12', 'been 2/12', 'sent 2/12', ..., 'end 12/12']
 * /
```

<details>
<summary>Solution</summary>
<pre>
<script>
  const longText = `
  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent pretium, augue in iaculis semper, magna sem gravida odio, ut rhoncus lacus nulla a justo. Fusce mi elit, laoreet pulvinar est eu, pellentesque posuere orci. Mauris vehicula feugiat tellus, eget bibendum nibh iaculis non. Mauris condimentum vulputate felis non dictum. Morbi quis eros nec lacus sollicitudin pharetra ac ac turpis. Ut scelerisque leo augue, a ullamcorper velit porttitor ut. Phasellus hendrerit dui ipsum, non rhoncus arcu lobortis ut. Aliquam fringilla et diam sed finibus. Interdum et malesuada fames ac ante ipsum primis in faucibus. Nulla facilisi. Pellentesque feugiat ornare ligula, et bibendum tellus. In hac habitasse platea dictumst. Fusce a urna suscipit neque luctus faucibus sed a velit. Interdum et malesuada fames ac ante ipsum primis in faucibus. Nullam ex ipsum, luctus non nunc vel, porta tincidunt quam. Proin eu ullamcorper eros. Morbi laoreet tellus in posuere iaculis. Nam molestie et purus eget efficitur. Duis aliquam purus in eros volutpat lacinia. Mauris vulputate quis sem at elementum. Fusce dictum lectus id lectus iaculis, eu commodo sem tristique. Aenean consectetur auctor sem vitae iaculis. Cras mollis libero sit amet congue vulputate. Ut tempor tellus sed arcu vehicula, non interdum massa condimentum. Donec ultricies, libero hendrerit sollicitudin gravida, tortor nunc vehicula est, eu placerat ex nisl ultrices neque. Morbi in auctor nunc, pharetra posuere ante. Curabitur ac gravida urna. Curabitur aliquam pellentesque iaculis. Etiam molestie, quam id pretium iaculis, elit nisi tempor dui, eu efficitur lacus lacus at lacus. 
  `;
  const test = longText.replace(/[.,\/#!$%\^&\*;:{}=\-_`~()]/g, '');
  function splitText(text) {
    let str = text;
    const CHUNK_SIZE = 136;
    const CHUNKS_LENGTH = Math.ceil(str.length / CHUNK_SIZE);
    const result = [];
    let counter = 0;
    //  Go through a loop, until 'str' in not totally empty.
    while (str !== '') {
      let lastSpace = 0;
      // not sure what 'i < str.length' means here
      for (let i = 0; i < CHUNK_SIZE; i++) {
        //  Check every space in the 136 string and assign the last one to the lastSpace
        if (str[i] === ' ') {
          lastSpace = i;
        }
      }
      //  Increment global chunks counter
      counter++;
      /*
        Insert into the final array slice of the 'str' of the range of 136,
        but only if the word is full (border of slicing is always a space ('lastSpace'))
      */
      result.push(str.slice(0,lastSpace) + ` ${counter}/${CHUNKS_LENGTH}`);
      //  Update the global text copy by removing used slice
      str = str.slice(lastSpace);
    }
    //  test messages symbols length
    result.map((sms, i) => {
      console.log(`chunk_${i} = ${sms.length}`)
    });
    return result;
  };

</script>
<div>Complexity:</div>
<p><strong>log(N)</strong></p>
</pre>
</details>
