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
**2. 3Sum**
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:

        n = len(nums)
        res = []
        nums.sort()

        for i in range(n):
            
            #avoid processing duplicate, allow 1st
            if i > 0 and nums[i] == nums[i-1]:
                continue

            left = i+1
            right = n-1

            while left < right:

                total = nums[i] + nums[left] + nums[right]

                if total > 0:
                    right -= 1
                elif total < 0:
                    left += 1
                else:
                    res.append([nums[i],nums[left],nums[right]])
                    left += 1
                    right -= 1
                    #since i itself remove duplicate from front
                    # while nums[left] == nums[left-1] and left < right:
                    #     left += 1
                    while nums[right] == nums[right+1] and left < right:
                        right -= 1
            
        
        return res
```
**Remove Nth Node from End of List**
```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:

        fast = head
        for _ in range(n):
            # no need to delete case
            if not fast:
                return head
            fast = fast.next
        
        #single node case
        if not fast:
            return head.next

        slow = head
        #maintain a gap of n and stop last node
        while fast and fast.next:
            slow = slow.next
            fast = fast.next

        #delete 
        slow.next = slow.next.next
        
        return head 
```
