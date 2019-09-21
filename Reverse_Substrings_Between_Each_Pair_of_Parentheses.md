**Questions**

You are given a string s that consists of lower case English letters and brackets. 

Reverse the strings in each pair of matching parentheses, starting from the innermost one.

Your result should not contain any brackets.



**Examples**
```
Input: s = "(abcd)"
Output: "dcba"

Input: s = "(u(love)i)"
Output: "iloveu"
Explanation: The substring "love" is reversed first, then the whole string is reversed.

Input: s = "(ed(et(oc))el)"
Output: "leetcode"
Explanation: First, we reverse the substring "oc", then "etco", and finally, the whole string.

Input: s = "a(bcdefghijkl(mno)p)q"
Output: "apmnolkjihgfedcbq"
```


**KNOWLEDGE POINTS**

- This question need to understand a concept "STACK", [here](https://juejin.im/post/5b7c01c9e51d45388325208a) is python example
- pop() is stack function, and means remove the last one in list while return it 
- know that how reverse string by [::-1] should know how slice work: [three ways to reverse Python string] (https://www.jianshu.com/p/c61279736a03)

then you can get the solution below:


**Solutions**
```
res = ['']
for c in s:
    if c == '(':
        res.append('')
    elif c == ")":
        res[len(res) - 2] += res.pop()[::-1] # put the reverse string in -2 cause the -1 should be ''
    else:
        res[-1] += c
```

**Conclusions**

- this question is easy to misunderstand the string in bracket just reverse once, actually it will follow the parentheses to reverse, so try to find the regularity wisely.
- these is another solution about DFS, just mark blog [here](https://blog.csdn.net/qq_17550379/article/details/100915900)

**Refs**

