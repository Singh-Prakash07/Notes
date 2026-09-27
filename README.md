https://github.com/taogen-docs/resources-of-learning/blob/master/_cs-advanced-domains-resources.md

class Solution:
    def maximumScore(self, nums: list[int], k: int) -> int:
        n = len(nums)
        left = [-1]*n
        right = [n]*n
        stk = []
        for i, num in enumerate(nums):
            while stk and nums[stk[-1]]>num:
                stk.pop()
            if stk:
                left[i] = stk[-1]
            stk.append(i)
        stk = []
        for i in range(n-1, -1, -1):
            num = nums[i]
            while stk and nums[stk[-1]]>=num:
                stk.pop()
            if stk:
                right[i] = stk[-1]
            stk.append(i)
        ans = 0
        for i, num in enumerate(nums):
            if left[i]<=k and right[i]>=k:
                temp = (right[i]-left[i]-1)*num
                ans = max(ans, temp)
        return ans

        
