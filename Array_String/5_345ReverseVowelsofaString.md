# 345. Reverse Vowels of a String

Two point question

```python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        VOWELS = {'A', 'E', 'I', 'O', 'U', 'a', 'e', 'i', 'o', 'u'}
        char_list = list(s)
        start = 0
        end = len(char_list) - 1

        while start <= end:
            if (char_list[start] in VOWELS) and (char_list[end] in VOWELS):
                char_list[start], char_list[end] = char_list[end], char_list[start]
                
                start += 1
                end -= 1
            elif char_list[start] not in VOWELS:
                start += 1
            elif char_list[end] not in VOWELS:
                end -= 1
        
        return ''.join(char_list)
```

>[!TIP]
>
> char_list = list(s) and ''.join(char_list)

### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$
