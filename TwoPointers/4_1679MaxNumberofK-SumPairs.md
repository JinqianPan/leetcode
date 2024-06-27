# 1679. Max Number of K-Sum Pairs

Using collections.Counter.

```python

class Solution(object):
    def maxOperations(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """
        res = 0

        count = collections.Counter(nums)
        for key, value in count.items():
            if key * 2 == k:
                res += value // 2
            elif key * 2 < k and (k - key) in count:
                res += min(value, count[k-key])
        
        return res

```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(n)$
