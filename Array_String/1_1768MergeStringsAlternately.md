# 1768. Merge Strings Alternately

```python
class Solution(object):
    def mergeAlternately(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: str
        """
        word1_size = len(word1)
        word2_size = len(word2)

        if word1_size >= word2_size:
            loop_size = word2_size
            large_str = word1
            tmp = word1_size - loop_size
        else:
            loop_size = word1_size
            large_str = word2
            tmp = word2_size - loop_size

        result = ''
        for i in range(loop_size):
            result += word1[i]
            result += word2[i]
        
        for i in range(tmp):
            result += large_str[i+loop_size]
        
        return result
```