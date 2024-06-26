# 334. Increasing Triplet Subsequence

The simple way is

```python
class Solution(object):
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        for i in range(len(nums)):
            for j in range(i, len(nums)):
                if nums[i] < nums[j]:
                    for k in range(j, len(nums)):
                        if nums[j] < nums[k]:
                            return True
        
        return False
```
### Complexity
Time complexity: $O(n^3)$

Space complexity: $O(1)$

---
Tutorial: [bilibili](https://www.bilibili.com/video/BV1Cf4y1s7XM?p=2&vd_source=cbcc5c6e34f2945b72af2d7b154577b0)

If we use `j` as the point, we could let time complexity as $O(n^2)$
```python

class Solution(object):
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        nums_size = len(nums)
        first = False
        second = False

        for j in range(1, nums_size - 1):
            for i in range(j):
                if nums[i] < nums[j]:
                    first = True
                    break
                    
            if first == False:
                continue

            for k in range(j+1, nums_size):
                if nums[j] < nums[k]:
                    second = True
                    break
            
            if (first == True) and (second == True):
                return True
            
            first = False
            second = False
        
        return False

```
### Complexity
Time complexity: $O(n^2)$

Space complexity: $O(1)$

---
Greedy

```python
class Solution(object):
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        first, second = float('inf'), float('inf')

        for i in range(len(nums)):
            if nums[i] <= first:
                first = nums[i]
            elif nums[i] <= second:
                second = nums[i]
            else:
                return True
        
        return False
```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$