# Top-100-most-asked-leetcode-questions-in-coding-interviews-


### Question 1
Arrays   Bit Manipulation

Question:
[Write a program which will find all such numbers which are divisible by 7 but are not a multiple of 5, between 2000 and 3200 (both included).
The numbers obtained should be printed in a comma-separated sequence on a single line.](https://leetcode.com/problems/missing-number/description/)

Hints: 
Consider use range(#begin, #end) method

Solution:
```python
l=[]
for i in range(2000, 3201):
    if (i%7==0) and (i%5!=0):
        l.append(str(i))

print(','.join(l))
```
