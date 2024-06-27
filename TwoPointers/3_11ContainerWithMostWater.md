# 11. Container With Most Water

```python

class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_area = 0

        for i in range(len(height)):
            for j in range(i+1, len(height)):
                if height[i] < height[j]:
                    low = height[i]
                else:
                    low = height[j]
                weight = j - i

                area = low * weight

                if area > max_area:
                    max_area = area
        
        return max_area

```

### Complexity
Time complexity: $O(n^2)$

Space complexity: $O(1)$

---

This two point is from left and right.

```python

class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_area = 0

        left, right = 0, len(height)-1
        while left < right:
            area = min(height[left], height[right]) * (right - left)
            max_area = max(max_area, area)
            if height[left] > height[right]:
                right -= 1
            else:
                left += 1
        return max_area

```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$