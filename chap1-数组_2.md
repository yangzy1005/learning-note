# chap1.数组

## 2.移除元素
* 暴力解法<br>
  时间复杂度：O(n^2) 空间复杂度：O(1)<br>
* 双指针法<br>***常见 熟知***
  快指针：寻找新数组的元素 ，新数组就是不含有目标元素的数组<br>
  慢指针：指向更新新数组下标的位置//下一个待处理的位置<br>
  时间复杂度：O(n) 空间复杂度：O(1)<br

### **27:easy:移除元素**
```
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow, fast, size = 0, 0, len(nums)
        while fast < size:
            if nums[fast] != val:
                nums[slow] = nums[fast]
                slow += 1
            fast += 1
        return slow
```   
### **26:easy:删除排序数组中的重复项**
```
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        slow, fast, size = 1, 1, len(nums)

        while fast < size:
            if(nums[fast] != nums[fast-1]):
                nums[slow] = nums[fast]
                slow += 1
            fast += 1
        return slow
```
### **283::移动零**
```
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        slow, fast, size = 0, 0, len(nums)
        while fast < size:
            if nums[fast] != 0:
                nums[slow] = nums[fast]
                slow += 1
            fast += 1
        while slow < size:
            nums[slow] = 0
            slow += 1
```
### **844::比较含退格的字符串**
```
```
### **977::比较含退格的字符串**

