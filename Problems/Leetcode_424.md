

## 1. [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

Explanation: https://blog.csdn.net/fuxuemingzhu/article/details/79527303

**Solution**
```
def longest_substring(s: str, k: int) -> int:
    from collections import defaultdict
    
    left = 0
    max_length = 0
    max_count = 0
    char_freq = defaultdict(int)
    
    for right in range(len(s)):
        char_freq[s[right]] += 1
        
        max_count = max(max_count, char_freq[s[right]])
        # print(char_freq, "right: %s"%right, "left: %s"%left, "max_count: %s"%max_count)
        # If the number of replacements needed is greater than k, shrink the window
        if (right - left + 1) - max_count > k:
            print("enter if logic")
            char_freq[s[left]] -= 1
            left += 1
        
        max_length = max(max_length, right - left + 1)
    
    return max_length

# Test cases
print(longest_substring("ABAB", 2))  # Output: 4
print(longest_substring("AABABBA", 1))  # Output: 4
```
