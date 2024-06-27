# 392. Is Subsequence

```python

class Solution(object):
    def isSubsequence(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        if len(s) == 0:
            return True

        point = 0
        count = 0
        for i in range(len(s)):
            while point < len(t):
                if s[i] == t[point]:
                    count += 1
                    point += 1
                    if count == len(s):
                        return True
                    break
                else:
                    point += 1
        
        return False

```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$


```python

class Solution(object):
    def isSubsequence(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        s_point, t_point = 0, 0

        while s_point < len(s) and t_point < len(t):
            if s[s_point] == t[t_point]:
                s_point += 1
            t_point += 1

        return s_point == len(s)

```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$