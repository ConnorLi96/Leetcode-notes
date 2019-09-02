A dieter consumes calories[i] calories on the i-th day.  For every consecutive sequence of k days, they look at T, the total calories consumed during that sequence of k days:

If T < lower, they performed poorly on their diet and lose 1 point; 
If T > upper, they performed well on their diet and gain 1 point;
Otherwise, they performed normally and there is no change in points.
Return the total number of points the dieter has after all calories.length days.

Note that: The total points could be negative.


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
