**Q**
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

**Explaination:** 



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



**Solution version 2:**
```
```
