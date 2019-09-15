**Questions**
Given a string text, you want to use the characters of text to form as many instances of the word "balloon" as possible.

You can use each character in text at most once. Return the maximum number of instances that can be formed.


**Examples:**

```
Input: text = "nlaebolko"
Output: 1


Input: text = "loonbalxballpoon"
Output: 2

Input: text = "leetcode"
Output: 0
```

**Solution1:**

import counter to calculate the frequency of each character in string, the 'l' and 'n' definitely is the double of other character, so just get min of counter list

```
from collections import Counter 
c = Counter(list(text))
return min([c[b],c[a],c[l]//2,c[o]//2, c[n]])

```

**Solution2:**

for loop the all string'balloon', and use the count of each character to calculate min possibilities.
```
from collections import Counter 
class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        cnt = 0
        freq_dict = Counter(list(text))
        
        while 1:
            for key in list("balloon"):
                if freq_dict[key] > 0:
                    freq_dict[key] -= 1
                else:
                    return cnt
                if key == "n":
                    cnt += 1

```


**Conclusion:**

Think this kind of problems by get the min of possibilities.

