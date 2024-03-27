## what is an Algorithm?

a process or set of steps to accomplish a certain task

## Interview

### How do you improve?

- Devise a plan for solving problems
- Master common problems solving patters

### Problem Solving

- understand the problem
- explore Concrete Examples
- Break it down
- solve/simplify
- look back and refactor

## UNDERSTAND THE PROBLEM

- Can I restate the problem in my own words?
- What are the inputs that go into the problem?
- What are the outputs that should come from the solution to the problem?
- Can the outputs be determined from the inputs? In other words, do I have enough information to solve the problem? (you
  may not be able to answer this question until you set about solving the problem. That's okay; it's still worth
  considering the question at this early stage.)
- How should I label the important pieces of data that are a part of the problem?

### Simple Example

"Write a function which takes two numbers and returns their sum."

- Can I restate the problem in my own words?
    - "implement addition"
- What are the inputs that go into the problem?
    - "integers? floats? what about string for large numbers?"
- what are the outputs that should come from the solution?
    - "integers? float? string?"
- Can the outputs be determined from the inputs? in other words, do I have enough information to solve the problem?
- How should I label the important pieces of data that are a part of the problem?

## Explore Concrete Examples

- coming up with eamples can help you understand the problem better
- Examples also provide sanity checks that your eventual solution works how it should

### Explore Examples

- start with simple examples
- Progress to more complex examples
- Explore examples with empty inputs
- Explore examples with invalid inputs

"Write a function which takes in a string and returns counts of each character in the string"

```js
charCount("aaaa"); //{a:4}
charCount("hello"); //{h:1,e:1,l:2,o:1}

"My phone number is 7049123344"// is this valid input?
"Hello hi" // do we count capitalizaion

charCount() // no input
charCount("") // empty string?
```

## Break it Down

- explicitly write out the steps you need to take

```js
//Write a function which takes in a string and returns counts of each character in the string
charCount("aaaa");
// {
//     a:4
// }

charCount("hello");
// {
//     h:1,
//     e:1,
//     l:2,
//     o:1    
// }

charCount("Your PIN number is 1234!");
// {
//     1:1,
//     2:1,
//     3:1,
//     4:1,
//     ...etc    
// }

function charCount() {
    //do something
    // return an object with keys that are lowercase alphanumeric characters in the string; values should be the characters in the string
}

function charCount() {
    // make object to return at end
    // loop over string, for each character...
    // if the char is a number/letter AND is a key in object, add one to count
    // if the char is a number/letter AND not in the object, add it to the object and set value to 1
    // if char is something else (space, period, etc.) don't do anything
    // return object at end 
}

```

## Break it down

"Solve the problem, if you can't... solve a simpler problem"

## Simplify

- find the core difficulty in what you are trying to do
- temporarily ignore that difficulty
- write a simplified solution
- then incorporate that difficulty back in

... going back to the "charCount()"

```js
  function charCount(str) {
    // make object to return at end
    var result = {}
    // loop over string, for each character...
    for (var i = 0; i < str.length; i++) {
        var char = str[i].toLowerCase();
        // if the char is a number/letter AND is a key in object, add one to count
        if (result[char] > 0) {
            result[char]++;
        }
        // if the char is a number/letter AND not in the object, add it to the object and set value to 1
        else {
            result[char] = 1;
        }
    }
    // if char is something else (space, period, etc.) don't do anything
    // return object at end 
    return result;
}
```

## Look Back & Refactor

### Refactoring Questions

- can you check the result
- can you derive the result differently
- can you understand it at a glance?
- can you use the result or method for some other problem?
- can you improve the performance of your solution?
- can you think of other ways to refactor
- how have other people solved this problem?

```js
function charCount(str) {
    var obj = {};
    for (var i = 0; i < str.length; i++) {
        var char = str[i].toLowerCase()
        if (/[a-z0-9]/.test(char)) {
            if (obj[char] > 0) {
                obj[char]++;
            } else {
                obj[char]
            }
        }
    }
    return obj;
}

function charCount(str) {
    var obj = {};
    for (var char of str) {
        char = char.toLowerCase()
        if (/[a-z0-9]/.test(char)) {
            if (obj[char] > 0) {
                obj[char]++;
            } else {
                obj[char]
            }
        }
    }
    return obj;
}

function charCount(str) {
    var obj = {};
    for (var char of str) {
        char = char.toLowerCase()
        if (/[a-z0-9]/.test(char)) {
            obj[char] = ++obj[char] || 1
        }
    }
    return obj;
}
```