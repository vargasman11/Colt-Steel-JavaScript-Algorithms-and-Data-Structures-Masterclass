[# Problem Solving Patters

- Frequency counter
- Multiple Pointers
- Sliding Windows
- Divide and Conquer
- Dynamic Programming
- Greedy Algorithms
- Backtracking
- ... more!

## Frequency Counter Patter

This pattern uses objects or sets to collect values/frequencies of values

This can often avoid the need for nested loops or O(N^2) operations with arrays/strings.

### An Example

Write a function called same, which accepts two arrays. The function should return true if every value in the array has
its corresponding value squared in the second array. The frequency of values must be the same.

```js
same([1, 2, 3], [4, 1, 9]) //true
same([1, 2, 3], [1, 9]) //false
same([1, 2, 1], [4, 4, 1]) //false (must be same frequency)
```

#### A Naive Solution

```js
function same(arr1, arr2) {
    if (arr1.length !== arr2.length) {
        return false
    }
    for (var i = 0; i < arr1.length; i++) {
        let correctIndex = arr2.indexOf(arr1[i] ** 2)
        if (correctIndex == -1) {
            return false;
        }
        arr2.splice(correctIndex, 1)
    }
    return true
}

// Time Complexity =  N^2
```

#### Refactored

```js
function same(arr1, arr2) {
    if (arr1.length !== arr2.length) {
        return false;
    }
    let frequencyCounter1 = {}
    let frequencyCounter2 = {}
    for (let val of arr1) {
        frequencyCounter1[val] = (frequencyCounter1[val] || 0) + 1
    }
    for (let val of arr2) {
        frequencyCounter2[val] = (frequencyCounter2[val] || 0) + 1
    }
    for (let key in frequencyCounter1) {
        if (!(key ** 2 in frequencyCounter2)) {
            return false
        }
        if (frequencyCounter2[key ** 2] !== frequencyCounter1[key]) {
            return false
        }
    }
    return true;
}

//Time Complexity - O(n)

// Two loops is vastly better two nest loops
```

### Anagrams

Given two strings, write a function to determine if the second strgin is an anagram of the first. An anagram is a word
or phrase or name formed by rearranging the letters of another, such as cinema, formed from iceman.

```js
validAnagram('', '') // true
validAnagram('aaz', 'zza') // false
validAnagram('anagram', 'nagaram') // true
validAnagram("rat", "car") // false) // false
validAnagram('awesome', 'awesom') // false
validAnagram('amanaplanacanalpanama', 'acanalmanplanpamana') // false
validAnagram('qwerty', 'qeywrt') // true
validAnagram('texttwisttime', 'timetwisttext') //
```

### Multiple Pointers Pattern

Creating pointers or values that correspond to an index or position and move towards the beginning or end or middles
based on a certain condition. Very efficient for solving problems with minimal space complexity as well.

#### An Example

write a function called sumZero which accepts a sorted array of integers. The function should find the first pair where
the sum is 0. Return an array that includes both values that sum to zero or undefined if a pair does not exist.

```js
sumZero([-3, -2, -1, 0, 1, 2, 3,]) //[-3,3]
sumZero([-2, -1, 0, 1, 3,]) // undefined
sumZero([1, 2, 3,]) // undefined
```

```js
// Naive Solution
function sumZero(arr) {
    for (var i = 0; i < arr.length; i++) {
        for (var j = 0; j < arr.length; j++) {
            if (arr[i] + arr[j] === 0) {
                return [arr[i], arr[j]];
                ph
            }
        }
    }
}

// Time complexity - O(N^2)
// Space complexity - O(1)

// Refacotr
function sumZero(arr) {
    let left = 0;
    let right = arr.length - 1;
    while (left < right) {
        let sum = arr[left] + arr[right];
        if (sum === 0) {
            return [arr[left], arr[right]]
        } else if (sum > 0) {
            right--;
        } else {
            left++;
        }
    }
}

// Time complexity - O(N)
// Space complexity - O(1)
```

### Count Unique Value

implement a function called countUniqueValues, which accepts a sorted array and counts the unique values in the array.
There can be negative numbers in the array, but it will always be sorted

```js
function countUniqueValues(arr) {
    if (arr.length === 0) return 0;
    var i = 0;
    for (var j = 1; j < arr.length; j++) {
        if (arr[i] !== arr[j]) {
            i++;
            arr[i] = arr[j];
        }
    }
    return i + 1;
}
```

### Sliding Window Pattern

this pattern involves creating a window which can either be an array or number from one position to another.
depending on a s certain conditions, the window either increases or closes (and a new window is created)
Very useful for keeping track of a subset of data in an array/string etc.

#### A Naive Solution

```js
function maxSubarraySum(arr, num) {
    if (num > arr.length) {
        return null
    }
    var max = -Infinity;
    for (var i = 0; i < arr.length - num + 1; i++) {
        temp = 0;
        for (var j = 0; j < num; j++) {
            temp += arr[i + j];
        }
        if (temp > max) {
            max = temp;
        }
    }
    return max;
}

// Time Complexity - O(N^2)
```

#### Refactor

```js
function maxSubarraySum(arr, num) {
    let maxSum = 0;
    let tempSum = 0;
    if (arr.length < num) return null;
    for (let i = 0; i < num; i++) {
        maxSum += arr[i];
    }
    tempSum = maxSum;
    for (let i = num; i < arr.length; i++) {
        tempSum = tempSum - arr[i - num] + arr[i];
        maxSum = Math.max(maxSum, tempSum);
    }
    return maxSum;
}

// Time Complexity - O(N)
```

### Divide and Conquer

This pattern involves dividing a data set into smaller chunks and then repeating a process with a subset of data.

this patter can tremendously decrease time complexity

#### An example

Given a sorted array of intergers, write a function called search, that accepts a value and returns the index where the
value passed to the function is located. If the value is not found, return -1

```js
search([1, 2, 3, 4, 5, 6], 4) // 3
search([1, 2, 3, 4, 5, 6], 6) // 5
search([1, 2, 3, 4, 5, 6], 11) // -1
```

#### A Naive Solution

```js
function search(arr, val) {
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] === val) {
            return i;
        }
    }
    return -1
}

// Linear Search

//Time Complexity O(N)
```

#### Refactor

```js
function search(array, val) {
    let min = 0;
    let max = array.length - 1;

    while (min <= max) {
        let middle = Math.floor((min + max) / 2);
        let currentElement = array[middle];

        if (array[middle] < val) {
            min = middle + 1;
        } else if (array[middle] > val) {
            max = middle - 1;
        } else {
            return middle;
        }
    }
    return  -1
}

//Time Complexity - Log(N) - Binary Search
```








