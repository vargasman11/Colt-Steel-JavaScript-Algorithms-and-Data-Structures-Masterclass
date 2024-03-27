## The Big O of Objects

Objects are unordered, key value pairs

### When to use objects

- work well when you don't need order
- when you need fast access / insertion and removal

### Big O of Objects

Inertion - O(1)
Removal - O(1)
Searching - O(1)
Access - O(1)

when you dont need any ordering, objects are an excellent choice.

### Big O of Object Methods

Object.keys - O(N)
Object.values - O(N)
Object.entries - O(N)
hasOwnProperty - O(1)

## Arrays

Ordered Lists, intrinsic order to the data.

### When to use Arrays

- when you need order
- When you need fast access/ insertion and removal (sort of ...)

### Big O of Arrays

- insertion - it depends ...
- removal - ir depends...
- searching - O(n)
- Access - O(1)

inserting at the beginning of an array is costly because all elements in the array would have to be indexed. The same
goes for removing elements at the beginning, everything would have to be re-indexed.

### Big O of Arrays Methods
- push - O(1)
- pop - O(1)
- shift - O(n)
- unshift - O(n)
- concat - O(n)
- slice - O(n)
- splice - O(n)
- sort - O(N * log n)
- forEach/map/filter/reduce/etc - O(N)
