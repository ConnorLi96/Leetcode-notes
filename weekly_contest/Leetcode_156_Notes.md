### 1. Unique Number of Ocurrences 

**Questions**

Given an array of integers arr, write a function that returns true if and only if the number of occurrences of each value in the array is unique.

**Examples**
```
Input: arr = [1,2,2,1,1,3]
Output: true

Input: arr = [1,2]
Output: false

Input: arr = [-3,0,1,-3,1,1,1,-3,10,0]
Output: true

```
**KNOWLEDGE POINTS**
- the occurrences of each elements in list
- set, no repeat elements

**Solution1**
Just get the counter of each element in list, and then compare the length of ```set of result``` and the result, which could know there is  unique value in array or not
```
def solution_666(arr):
    ct = Counter(arr)
    return len(set(ct.values())) == len(ct.values())
```


### 2. Get Equal Substring Within Budget
**Questions**

You are given two strings s and t of the same length. You want to change s to t. Changing the i-th character of s to i-th character of t costs |s[i] - t[i]| that is, the absolute difference between the ASCII values of the characters.

You are also given an integer maxCost.

Return the maximum length of a substring of s that can be changed to be the same as the corresponding substring of twith a cost less than or equal to maxCost.

If there is no substring from s that can be changed to its corresponding substring from t, return 0.

**Examples**
```
Input: s = "abcd", t = "bcdf", maxCost = 3
Output: 3
Explanation: "abc" of s can change to "bcd". That costs 3, so the maximum length is 3.

Input: s = "abcd", t = "cdef", maxCost = 3
Output: 1
Explanation: Each character in s costs 2 to change to charactor in t, so the maximum length is 1.

Input: s = "abcd", t = "acde", maxCost = 0
Output: 1
Explanation: You can't make any change, so the maximum length is 1.
```

**KNOELEDGEMENT POINT**
- Slicing Window

**Solution**

```
```


### 3. Remove Adjacent Duplicates in String
**Questions**

Given a string ```s```, a ```k``` duplicate removal consists of choosing k adjacent and equal letters from s and removing them causing the left and the right side of the deleted substring to concatenate together.

We repeatedly make k duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made.

It is guaranteed that the answer is unique.


**Examples**
```
Input: s = "abcd", k = 2
Output: "abcd"
Explanation: There's nothing to delete.

Input: s = "deeedbbcccbdaa", k = 3
Output: "aa"
Explanation: 
First delete "eee" and "ccc", get "ddbbbdaa"
Then delete "bbb", get "dddaa"
Finally delete "ddd", get "aa"

Input: s = "pbbcggttciiippooaais", k = 2
Output: "ps"
```

**KNOELEDGEMENT POINT**
- STACK
    - put the char in stack and set the count of char as 1
    - if the last one, stack ```[-1]``` is equal to the next char, then the count += 1, until count == ```k```, and then remove this char.
    - else, keep put char in stack

**Solution**
```
stk = []
for item in s:
    if not stk or stk[-1][1] != item:
        stk.append([item,1])
    else:
        stk[-1][1] += 1
        if stk[-1][1] == k:
            stk.pop()
return "".join(item * index for item, index in stk) 
```


