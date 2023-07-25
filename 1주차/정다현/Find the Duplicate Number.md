### Find the Duplicate Number

링크: https://leetcode.com/problems/find-the-duplicate-number/

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        # 조건: constant extra space만 사용 가능 (map 사용 불가)
        # n이 10^5 이니까 nlogn까지 가능할 듯함
        # 개수가 n+1개일 때 [1, n]까지의 숫자가 들어있음.

        n = len(nums) - 1
        # binary search
        left = 1
        right = n

        while (left < right):
            mid = (left+right)//2
            less, equal = 0, 0
            for num in nums:
                if (num < mid): less += 1
                elif num == mid: equal += 1
            if (equal > 1): return mid
            if (less >= mid): right = mid - 1
            else: left = mid + 1

        return left
```
