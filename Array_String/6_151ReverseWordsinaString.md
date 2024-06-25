# 151. Reverse Words in a String

```python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        words = []
        word = ''
        s = ' ' + s + ' '

        for i in range(len(s)):
            if s[i] != ' ':
                word += s[i]
            else:
                if word != '':
                    words.append(word)
                word = ''
        
        result = words[0]
        for i in range(1, len(words)):
            result = words[i] + ' ' + result
        
        return result
```
### Complexity
Time complexity: $O(n)$

Space complexity: $O(n)$

```python
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        words = s.split()

        return ' '.join(words[::-1])
```
>[!TIP]
> s.split() will drop all ' '
>
> the result list need to use `join`
>
> array[::-1] is reverse

```python 
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """
        words = []
        i, end = 0, len(s)

        while i < end:
            if s[i] == ' ':
                i += 1
            else:
                word_start = i
                while (i < end) and (s[i] != ' '):
                    i += 1
                word = s[word_start:i]
                words.append(word)

        return ' '.join(words[::-1])
```
>[!TIP]
> Use two point

### Complexity
Time complexity: $O(n)$

Space complexity: $O(n)$