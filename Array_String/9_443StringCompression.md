# 443. String Compression

```python 
class Solution(object):
    def compress(self, chars):
        """
        :type chars: List[str]
        :rtype: int
        """
        res = 0
        count = 1
        for i in range(len(chars)):
            if (i+1 < len(chars)) and (chars[i] == chars[i+1]):
                count = count + 1
            else:
                chars[res] = chars[i]
                if count != 1:
                    res += 1
                    for j in str(count):
                        chars[res] = j
                        res += 1
                else:
                    res += 1
                count = 1
        return res
```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$