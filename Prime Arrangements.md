**Q:**
ber of permutations of ```1 to n``` so that prime numbers are at prime indices (1-indexed.)

(Recall that an integer is prime if and only if it is greater than 1, and cannot be written as a product of two positive integers both smaller than it.)

Since the answer may be large, return the answer modulo 10^9 + 7.

**Example:**
```
Input: n = 5
Output: 12
Explanation: For example [1,2,5,4,3] is a valid permutation, but [5,2,3,4,1] is not because the prime number 5 is at index 1.
```

```
Input: n = 100
Output: 682289015
```

**Constains:**
1 <= n <= 100


**Knowledge points:**
- jiecheng
- prime
- mod


**Question Analysis:**
let's put mod away, reminding consider it at last step. This kind of problems could be classified as permutation problem. According the example 1, the possible permutation examples P as below:

| 一个普通标题 | 一个普通标题 | 一个普通标题 |
| ------ | ------ | ------ |
| 短文本 | 中等文本 | 稍微长一点的文本 |
| 稍微长一点的文本 | 短文本 | 中等文本 |

| Possibities| example1| example2 | example3 | example4 | ...|
| permutation | [1,2,3,4,5] | [1,2,3,5,4] | [1,2,5,4,3] |[5,2,3,4,1] | ...|
| Index | [1,2,3,4,5] | [1,2,3,4,5] | [1,2,3,4,5] |[1,2,3,4,5] | ...|
| Work | valid | invalid | valid | invalid | ...|

Depends on the table, we get two points:


**Solutions**
```

```

