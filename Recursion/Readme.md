# Recursion

## What is Recursion?

A process (a function in our case) that calls itself

When we write recursive functions, we keep pushing new functions onto the call stack.

## How Recursive functions work?

Invoke the same function with a differenvt input until you reach your base case

- What's a base case?
    - The condition when the recursion ends. THIS IS THE MOST IMPORTANT CONCEPT TO UNDERSTAND

- Two Essential parts of a recursive function!
    - Base case
    - Different Input

### Our First Recursive function

```js
//RECURSIVE
function countDown(num) {
    if (num <= 0) {
        console.log("all done");
        return;
    }
    console.log(num)
    num--
    countDown(num)
}

//NON RECURSIVE
function countDown(num) {
    for (var i = num; i > 0; i--) {
        console.log(i)
    }
    console.log("All done!")
}
```

### Our Second Recursive function

```js
function sumRange(num) {
    if (num === 1) return 1;
    return num + sumRange(num - 1)
}
```
