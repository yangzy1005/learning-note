# chap1.数组

## 0.数组理论基础
* 存储空间连续（高维也连续顺下来）
* 相同数据类型、下标from 0
* 数组元素不能删，只能覆盖

## 1.二分查找
* 什么时候用二分查找：题目指出**有序、无重复**
* 注意明确区间定义：<br>
    左闭右闭：target在 [left, right] 区间<br>
    `while left <= right`<br> 
    `if nums[middle] > target: right = middle - 1`<br>
    ***只记一种***<br>
    ~~左闭右开：target在 [left, right) 区间<br>
    `while left < right`<br> 
    `if nums[middle] > target: right = middle`<br>~~

### **207:easy**    
```
class Solution:
    def Search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1

        while left <= right :
            middle = left + (right - left) // 2

            if nums[middle] < target :
                left = middle + 1
            elif nums[middle] > target :
                right = middle - 1
            else:
                return middle
        return -1
```
### **35:easy** 
```
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        low, high = 0, len(nums) - 1
        
        while low <= high :
            middle = low + (high - low) // 2

            if nums[middle] < target:
                low = middle + 1
            elif nums[middle] > target:
                high = middle - 1
            else:
                return middle
        
        return middle
```
### **34:medium** 
查找左右边界
```
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:
        def getRightBorder(nums: List[int], target: int) -> int:
            low, high = 0, len(nums) - 1
            rightBorder = -2

            while low <= high:
                middle = (low + high) // 2

                if nums[middle] <= target:
                    low = middle + 1
                    rightBorder = low
                else:
                    high = middle - 1

            return rightBorder
        
        def getLeftBorder(nums: List[int], target: int) -> int:
            low, high = 0, len(nums) - 1
            leftBorder = -2

            while low <= high:
                middle = (low + high) // 2

                if nums[middle] >= target:
                    high = middle - 1
                    leftBorder = high
                else:
                    low = middle + 1

            return leftBorder

        leftBorder = getLeftBorder(nums, target)
        rightBorder = getRightBorder(nums, target)

        #target不在数组范围内
        if leftBorder == -2 or rightBorder == -2: return [-1, -1]
        #target在数组范围内，且数组里存在target
        if rightBorder - leftBorder > 1: return [leftBorder + 1, rightBorder - 1]
        #target在数组范围内，但数组里不存在target
        return [-1, -1]

```
### **69:easy** 
谁能想到老子搞不懂的是这题
### **367:easy** 

