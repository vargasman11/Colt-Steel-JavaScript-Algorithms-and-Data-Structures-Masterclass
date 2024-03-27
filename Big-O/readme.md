constants dont matter

O(2n) = O(n)
O(500) = O(1)
O(13n^2) = O(n^2)

Smaller Terms Dont Matter

O(n + 10)  = O(n)
O(100n + 50)  = O(n)
O(n^2 + 5n + 8)  = O(n^2)

BIG O Shorthands

1) Arithmetic Operations are constant
2) Variable assignment is constant
3) Accessing Element in an awway (by index) or object (by key) is constant
4) in a loop, the complexity is the length of the loop times the complexity of whatever happens inside the loop.


The expression \( O(n^2 + n^3) \) simplifies to \( O(n^3) \) because in big O notation, we focus on the dominant term as the input size grows. In this case, as \( n^3 \) grows much faster than \( n^2 \), the \( n^3 \) term dominates. So, we can simplify the expression to just \( O(n^3) \).

# SPACE COMPLEXITY

most primatives(booleans, numbes, undefined, null) are constant space
String require O(n) space (where n is the string length)
Reference types are generally O(n), where n is the length (for arrays) or the number of keys (for Objects)