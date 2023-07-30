# Whiteboard Evaluation

## Description:
`Question 4`
Write an algorithm that determines whether all the elements in a string are unique. You may not convert the string into an array or use array methods to solve this problem. The algorithm should return a boolean.

```
Input: "hello"

Output: false

Input: "copyright"

Output: true
```

## Overview
1. Initialize an empty object 'seen' that will keep track of elements that have already been encountered.
2. Iterate over each character in the iunput string 'str'
3. In each iteration check if the character is in 'seen'
4. If it is, return false
5. If it's not, mark as seen in 'seen'
6. After the loop is complete, return true.

## Code
```
function isUnique(str) {
  let seen = {}
  for (let i = 0; i < str.length; i++) {
    if (seen[str[i]]) {
      return false;
    }
    seen.add();
  }
  return true;
}
```