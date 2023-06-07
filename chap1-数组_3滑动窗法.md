# chap1.数组

## 2.长度最小的子数组
* 暴力解：两个for，分别搜索子序列的起点和终点，时间复杂度O(n^2)<br>
* 滑动窗：**特别注意：while(for)套while(for)不一定就O(n^2)**，重要的是分析每个元素被操作几次，在滑动窗中，每个元素操作次数：进窗一次 + 出窗一次，操作次数2n，所以时间复杂度是O(n)<br>

### **209:medium:长度最小的子数组**
(暴力解法)<br>
```
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        minLen = float('inf')

        for i in range(len(nums)):
            sum = 0
            for j in range(i, len(nums)):
                sum += nums[j]
                if sum >= target:
                    Len = j - i + 1
                    minLen = min(Len, minLen)
                    break
        return minLen if minLen != float('inf') else 0
```
(滑动窗法)<br>
```
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        minLen = float('inf')
        size = len(nums)
        left, right = 0, 0
        SubSum = 0
        while(right < size):
            SubSum += nums[right]

            while(SubSum >= target):
                minLen = min(minLen, right - left + 1)
                SubSum -= nums[left]
                left += 1
            
            right += 1

        return minLen if minLen != float('inf') else 0
```
### **904:medium:水果成篮**
```
太难了再说吧
```
### **76:hard:最小覆盖子串**
```
```
