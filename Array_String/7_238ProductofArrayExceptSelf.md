# 238. Product of Array Except Self

The most simple way:
```python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        res = []
        res_num = 1
        for num in nums:
            for j in nums:
                if j != num:
                    res_num *= j
            res.append(res_num)
            res_num = 1
        
        return res
```

However, the time complexity is $O(n^2)$

There are some duplicate calculatings.

```python
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        pre = [1] * len(nums)
        post = [1] * len(nums)

        for i in range(1, len(nums)):
            pre[i] = pre[i-1] * nums[i-1]
        for i in range(len(nums)-2, -1, -1):
            post[i] = post[i+1] * nums[i+1]

        res = []
        for i in range(len(nums)):
            res.append(pre[i] * post[i])
        
        return res
```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(n)$

We also could let space complexity as $O(1)$.

```python 
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        res = [1] * len(nums)
        tmp = 1

        for i in range(1, len(nums)):
            res[i] = res[i-1] * nums[i-1]
        for i in range(len(nums)-2, -1, -1):
            tmp = tmp * nums[i+1]
            res[i] = res[i] * tmp
        
        return res
```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$