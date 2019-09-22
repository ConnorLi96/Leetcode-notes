**Question:**

Return the number of permutations of ```1 to n``` so that prime numbers are at prime indices (1-indexed.)

(Recall that an integer is prime if and only if it is greater than 1, and cannot be written as a product of two positive integers both smaller than it.)

Since the answer may be large, return the answer modulo ```10^9 + 7.```

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
- factorial
- prime
- permutation 


**Question Analysis:**
Let's put module away, just consider it at last step. This kind of problems could be classified as permutation problem. According the example 1, the possible permutation examples P as below:

| Possibities| example1| example2 | example3 | example4 |
| ------ | ------ | ------ | ------ | ------ |
| permutation | [1,2,3,4,5] | [1,2,3,5,4] | [1,2,5,4,3] | [5,2,3,4,1] | 
| Index | [1,2,3,4,5] | [1,2,3,4,5] | [1,2,3,4,5] | [1,2,3,4,5] |
| Work | valid | invalid | valid | invalid |

Depends on the table, we get two points:
- when the elements and its index are prime simultaneously means work.
- the permutation possibilities will be the n's factorial, 120 is the factorial result of n in this case
- when the permutation is valid, the prime number are the prime index, the plural number also are the plural index. 

So we can assume the ```p ``` as the number of prime number in the list ```1 to n```, so the plural number in the list n will be ```n - p```. And the valid permutation will be factorial of ```p``` * factorial of ```n -p ```.

In conclusion, the solution steps are:
- count the sum of prime number in list ```1 -n```
- result = factorial (p) * factorial (n-p)
- return  ``` result mod 10^9 + 7```



**Solutions**
```
def numPrimeArrangements(self, n):

    def count_prime(n):
        num=[]
        for item in range(2,n+1):
            for j in range(2,item):
                if(item%j==0):
                    break
            else:
                num.append(item)
        return len(num)

    prime_number = count_prime(n)

    ans = (math.factorial(prime_number) * math.factorial(n-prime_number))
    return ans % (10**9+7)
```


**Factorial implementation in Python**
```
case1:
a = 1
n = 5
for i in range(1,n+1):
    a = a * i
print(a)


case2: 
def factorial(n):
  if n ==1 or n ==0:
    return 1
  else:
    return (n * factorial(n))
```
