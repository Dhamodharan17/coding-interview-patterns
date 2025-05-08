List - https://leetcode.com/problem-list/2z6blu1e/

**1.Valid Palindrome**
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:

        start, end = 0, len(s)-1

        while start < end:

            if not s[start].isalnum():
                start += 1
                continue # even next can be not alpha num
            if not s[end].isalnum():
                end -= 1
                continue
            
            if s[start].lower() != s[end].lower():
                return False
            
            start += 1
            end -= 1
        
        return True
```
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = ''.join(c.lower() for c in s if c.isalnum())
        left = 0
        right = len(s)-1

        while left < right:
            if s[left] != s[right]:
                return False
            left +=1
            right -=1
        
        return True
```
