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
