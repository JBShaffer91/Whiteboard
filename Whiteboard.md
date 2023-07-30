# Welcome to the Whiteboard

## Question #1: Turning Strings to URLs

### Description:
URLs cannot have spaces. Instead, all spaces in a string are replaced with %20. Write an algorithm that replaces all spaces in a string with %20.

You may not use the replace() method or regular expressions to solve this problem. Solve the problem with and without recursion.

Example:
```
Input: "Jasmine Ann Jones"

Output: "Jasmine%20Ann%20Jones"
```

### Non-Recursive Solution:
Use a for loop to iterate over each character in the string. If the character is a space, add %20 to the new string. Otherwise, add the character to the new string.

### Overview:

1. Initialize an empty string `result` that will hold the final result.
2. Iterate over each character in the input string `str`.
3. In each iteration, check if the character is a space.
4. If it is, append `%20` to `result`.
5. If it's not a space, append the character itself to `result`.
6. After the loop is complete, return `result`.

### Code:
```js
function replaceSpaces(str) {
  let result = '';
  for (let i = 0; i < str.length; i++) {
    if (str[i] === ' ') {
      result += '%20';
    } else {
      result += str[i];
    }
  }
  return result;
}
```

### Recursive Solution:
Check the first character in the string, and then recursively call itself on the rest of the string (i.e., the string with the first character removed). The base case for the recursion is when the string is empty, in which case it returns an empty string.

### Overview:

1. Check if the string is empty. If it is, return an empty string.
2. If the string is not empty, check if the first character is a space.
3. If it is, return `%20` + the result of calling the function on the rest of the string.
4. If it's not a space, return the first character + the result of calling the function on the rest of the string.

### Code:
```js
function replaceSpacesRecursive(str) {
  if (str.length === 0) {
    return '';
  }
  return (str[0] === ' ' ? '20' : str[0]) + replaceSpacesRecursive(str.slice(1));
}
```

## Question #2: Array Deduping

### Description:
Write an algorithm that removes duplicates from an array. Do not use a function like filter() to solve this. Once you have solved the problem, demonstrate how it can be solved with filter(). Solve the problem with and without recursion.

Example:
```
Input: [7, 9, "hi", 12, "hi", 7, 53]

Output: [7, 9, "hi", 12, 53]
```

### Non-Recursive Solution:
Use a for loop to iterate over each element in the array. It should also use an object `seen ` to keep track of elements that have already been encountered. If an element is not in `seen`, it is added to the `result` array and marked as deen in `seen`. This way any duplicates will not be added to the `result` array.

### Overview:

1. Initialize an empty object `seen` that will keep track of elements that have already been encountered.
2. Initialize an empty array `result` that will hold the final result.
3. Iterate over each element in the input array `arr`.
4. In each iteration, check if the element is in `seen`.
5. If it is not, add it to `result` and mark it as seen in `seen`.
6. After the loop is complete, return `result`.

### Code:
```js
function dedupeArray(arr) {
  let seen = {};
  let result = [];
  for (let i = 0; i < arr.length; i++) {
    if (!seen[arr[i]]) {
      result.push(arr[i]);
      seen[arr[i]] = true;
    }
  }
  return result;
}
```

### Recursive Solution:
Check the first element in the array, and then recursively call itself on the rest of the array (i.e., the array with the first element removed). The base case for the recursion is when the array is empty, in which case it returns an empty array.

### Overview:

1. Check if the array is empty. If it is, return `result`.
2. Check if the first element is in `seen`.
3. If it is not, add it to `result` and mark it as seen in `seen`.
4. Return the result of calling the function on the rest of the array, with the updated `seen` and `result`.

### Code:
```js
function dedupeArrayRecursive(arr, seen = {}, result = []) {
  if (arr.length === 0) {
    return result;
  }
  if (!seen[arr[0]]) {
    result.push(arr[0]);
    seen[arr[0]] = true;
  }
  return dedupeArrayRecursive(arr.slice(1), seen, result);
}
```

## Question #3: Compressing Strings

Description: Write an algorithm that takes a string with repeated characters and compresses them, using a number to show how many times the repeated character has been compressed. For instance, aaa would be written as 3a. Solve the problem with and without recursion.

Example:
```
Input: "aaabccdddda"

Output: "3ab2c4da"
```

### Non-Recursive Solution:
Use a for loop to iterate over each character in the string. It should keep a count of the number of times the current character is repeated. If the next character is the same as the current one, it should increment the count. If the next character is different, it should add the count and the current character to the result of the string and reset the count to 1.

### Overview:

1. Initialize an empty string `result` that will hold the final result and a count variable to 1.
2. Iterate over each character in the input string `str`, starting from the second character.
3. In each iteration, check if the current character is the same as the previous character.
4. If it is, increment the count.
5. If it's not, add the count and the previous character to `result` and reset the count to 1.
6. After the loop is complete, return `result`.

### Code:
```js
function compressString(str) {
  let result = '';
  let count = 1;
  for (let i = 1; i <= str.length; i++) {
    if (str[i] === str[i - 1]) {
      count++;
    } else {
      result += count + str[i - 1];
      count = 1;
    }
  }
  return result;
}
```

### Recursive Solution:
Check the first character in the string, and then recursively call itself on the rest of the string (i.e., the string with the first character removed). The base case for the recursion is when the string is empty, in which case it returns an empty string.

### Overview:

1. Check if the string is empty. If it is, return an empty string.
2. If the string is not empty, check if the first character is the same as the second character.
3. If it is, return the result of the recursive call on the rest of the string, with the count incremented by 1.
4. If it's not, return the result of the recursive call on the rest of the string, with the count reset to 1, and add the count and the first character added to `result`.

### Code:
```js
function compressStringRecursive(str, count = 1, result = '') {
  if (str.length === 0) {
    return result;
  }
  if (str[0] === str[1]) {
    return compressStringRecursive(str.slice(1), count + 1, result);
  } else {
    return compressStringRecursive(str.slice(1), 1, result + count + str[0]);
  }
}
```

## Question #4: Checking for Uniqueness

Description: Write an algorithm that determines whether all the elements in a string are unique. You may not convert the string into an array or use array methods to solve this problem. The algorithm should return a boolean.

Example:
```
Input: "hello"

Output: false

Input: "copyright"

Output: true
```

### Non-Recursive Solution:
Use a for loop to iterate over each character in the string. It should also use an object `seen ` to keep track of elements that have already been encountered. If a character is in `seen`, it means the character is not unique and the function returns false. If a character is not in `seen`, it is marked as seen in `seen`. If the function finishes checking all characters and hasn't returned false, it means all characters are unique and the function returns true.

### Overview:

1. Initialize an empty object `seen` that will keep track of elements that have already been encountered.
2. Iterate over each character in the input string `str`.
3. In each iteration, check if the character is in `seen`.
4. If it is, return false.
5. If it's not, mark it as seen in `seen`.
6. After the loop is complete, return true.

### Code:
```js
function isUnique(str) {
  let seen = {};
  for (let i = 0; i < str.length; i++) {
    if (seen[str[i]]) {
      return false;
    }
    seen[str[i]] = true;
  }
  return true;
}
```
### Recursive Solution:
Check the first character in the string, and then recursively call itself on the rest of the string (i.e., the string with the first character removed). The base case for the recursion is when the string is empty, in which case it returns true.

### Overview:

1. Check if the string is empty. If it is, return true.
2. If the string is not empty, check if the first character is in the rest of the string.
3. If it is, return false.
4. If it's not, return the result of the recursive call on the rest of the string.

### Code:
```js
function isUniqueRecursive(str) {
  if (str.length === 0) {
    return true;
  }
  if (str.slice(1).includes(str[0])) {
    return false;
  }
  return isUniqueRecursive(str.slice(1));
}
```
## Question #5: Array Sorting

Write an algorithm that sorts an array without using the sort() method. There are many different sorting algorithms — take the time to read about the following:

Quick sort
Merge sort
Heap sort
Insertion sort
Bubble sort
Selection sort
You may implement any of the above algorithms (or your own) to solve the problem — as long as it doesn't use sort().

Example:
```
Input: [9, 2, 7, 12]

Output: [2, 7, 9, 12]
```

### Solution:
Use the Bubble Sort algorithm that repeatedly steps through the list and compares adjacent elements, swapping them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

### Overview:

1. Get the length of the array and store it in `len`.
2. Start a loop that runs `len` times. This loop will represent the number of passes through the array.
3. In each pass, start another loop that goes up to `len - i - 1`. After each pass, the largest element gets bubbled up to the end of the array, so we don't need to check the last `i` elements in the `i`th pass.
4. In each iteration of the inner loop, compare the current element `arr[j]` with the next element `arr[j + 1]`.
5. If `arr[j]` is greater than `arr[j + 1]`, swap them by storing `arr[j]` in a temporary variable `temp`, then setting `arr[j]` to `arr[j + 1]`, and then setting `arr[j + 1]` to `temp`.
6. After the inner loop is complete, the largest element in the array will be at the end of the array. So, after the outer loop is complete, the array will be sorted.

### Code:
```js
function bubbleSort(arr) {
  let len = arr.length;
  for (let i = 0; i < len; i++) {
    for (let j = 0; j < len - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        let temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
      }
    }
  }
  return arr;
}
```
