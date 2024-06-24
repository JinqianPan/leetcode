# 605. Can Place Flowers

```python
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        zero_count = 0
        count_one = 0
        if (flowerbed[0] == 0) and (len(flowerbed) == 1):
            n -= 1

        for i in range(len(flowerbed)-1, -1, -1):
            if flowerbed[i] == 0:
                zero_count += 1
            elif (flowerbed[i] == 1):
                count_one += 1
                if zero_count >= 2:
                    if count_one <= 1:
                        n = n - (zero_count // 2)
                    else:
                        n = n - ((zero_count - 1) // 2)
                zero_count = 0
            if i == 0:
                if zero_count >= 2:
                    n = n - ((zero_count+1) // 2)

        if n > 0:
            return False
        else:
            return True
```

### Complexity
Time complexity: $O(n)$

Space complexity: $O(1)$

However, this question does not need loop from the last.

```python 
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        zero_count = 0
        num_one = 0
        for i in flowerbed:
            if i == 0:
                zero_count += 1
            else:
                num_one += 1

                if num_one <= 1:
                    n = n - (zero_count // 2)
                else:
                    n = n - ((zero_count - 1) // 2)
                if n <= 0:
                    return True

                zero_count = 0

        if num_one == 0:
            n = n - ((zero_count + 1) // 2)
        else:
            n = n - (zero_count // 2)

        if n <= 0:
            return True
        else:
            return False
```

Easy thinking way: [Youtube](https://www.youtube.com/watch?v=ZGxqqjljpUI)
```python 
class Solution(object):
    def canPlaceFlowers(self, flowerbed, n):
        """
        :type flowerbed: List[int]
        :type n: int
        :rtype: bool
        """
        tmp_flowerbed = [0] + flowerbed + [0]
        for i in range(1, len(tmp_flowerbed)-1):
            if (tmp_flowerbed[i-1] == 0) and (tmp_flowerbed[i] == 0) and (tmp_flowerbed[i+1] == 0):
                n -= 1
                tmp_flowerbed[i] = 1
        return n <= 0
```