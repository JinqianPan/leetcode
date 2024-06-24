# 1431. Kids With the Greatest Number of Candies


```python
class Solution(object):
    def kidsWithCandies(self, candies, extraCandies):
        """
        :type candies: List[int]
        :type extraCandies: int
        :rtype: List[bool]
        """
        extra_list = []
        max_candies = 0
        for i in candies:
            extra_list.append(i + extraCandies)
            if i > max_candies:
                max_candies = i
        
        result = []
        for i in extra_list:
            if i >= max_candies:
                result.append(True)
            else:
                result.append(False)
        
        return result
```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(n)$