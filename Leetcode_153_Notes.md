
### Prime Arrangements

**Question:**

Return the number of permutations of ```1 to n``` so that prime numbers are at prime indices (1-indexed.)

(Recall that an integer is prime if and only if it is greater than 1, and cannot be written as a product of two positive integers both smaller than it.)

Since the answer may be large, return the answer modulo ```10^9 + 7.```

**Examples:**
```
Input: n = 5
Output: 12
Explanation: For example [1,2,5,4,3] is a valid permutation, but [5,2,3,4,1] is not because the prime number 5 is at index 1.
```

```
Input: n = 100
Output: 682289015
```


**Knowledge points:**
- factorial:
- prime:
- permutation: 


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


### Diet Performance 
**Questions**

A dieter consumes ```calories[i]``` calories on the i-th day.  For every consecutive sequence of ```k``` days, they look at ```T```, the total calories consumed during that sequence of k days:

If T < ```lower```, they performed poorly on their diet and lose 1 point; 
If T > ```upper```, they performed well on their diet and gain 1 point;
Otherwise, they performed normally and there is no change in points.
Return the total number of points the dieter has after all calories.length days.

Note that: The total points could be negative.

**Example1:**
```
Input: calories = [1,2,3,4,5], k = 1, lower = 3, upper = 3
Output: 0
Explaination: calories[0], calories[1] < lower and calories[3], calories[4] > upper, total points = 0.
```


**Example2:**
```
Input: calories = [6,5,0,0], k = 2, lower = 1, upper = 5
Output: 0
Explaination: calories[0] + calories[1] > upper,calories[1] + calories[2] =upper, calories[2] + calories[3] < lower, total points = 0.

## The description has been improved cause last version is a littile bit confused.
```


**Steps:**

- accroding the number of k to slice the list
- judge the valid elements in list 
- calculate the sum of single element 
- compare the sum with lower and upper
- return the sum of compared result


**Solution version 1: Time Limited**

Reason: ```sum()``` means another for loop, so there are two for loops in this function, which means the time of calculate will increase exponentially. Thus, when we can delete the first element and add the next element to calculate the sum.

Here is formula derivation：

```
The sum of T: [Calories[i] +Calories[i+1] + ... +  Calories[i+k]]
The sum of T2: [Calories[i+1] + ... +  Calories[i+k] + Calories[i+k+1]]

T2 - T:  Calories[i+k+1] + Calories[i]
```

```
class Solution(object):
    def dietPlanPerformance(self, calories, k, lower, upper):   
        single_score= []
        for item in [calories[i:i+k] for i in range(0,len(calories))]:

            if len(item) < k:
                pass
            else:
                if sum(item) < lower:
                    single_score.append(-1)
                if sum(item) > upper:
                    single_score.append(1)
            continue
        
        return sum(single_score)
```



**Solution version 2: Time Limited**
```
    def dietPlanPerformance(self,calories, k, lower, upper):   
        single_score= []



        for item in [calories[i:i+k] for i in range(0,len(calories))]:
            if len(item) < k:
                pass

            elif k==1:

                if item[0] < lower:
                    single_score.append(-1)
                if item[0] > upper:
                    single_score.append(1)

            else:
                left = 0
                right = k
                sum_item = 0
                for i in item[left:right]:
                    sum_item = sum_item+i 


                left += 1
                right += 1
                print(left)
                print(right)
                print(sum_item)

                if sum_item < lower:
                    single_score.append(-1)
                if sum_item > upper:
                    single_score.append(1)
            continue

        return sum(single_score)
```
