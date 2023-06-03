# chap1.数组

## 2.移除元素
* 暴力解法<br>
  时间复杂度：O(n^2) 空间复杂度：O(1)<br>
* 双指针法     ***常见 熟知***<br>
  快指针：寻找新数组的元素 ，新数组就是不含有目标元素的数组<br>
  慢指针：指向更新新数组下标的位置//下一个待处理的位置<br>
  时间复杂度：O(n) 空间复杂度：O(1)<br>

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
python数组类型——列表（list）:<br>
* `append()` : 把新元素加到list的末尾<br>
* `insert(index, item)` : 把item添加到位于索引号index的位置<br>
* `pop()` : 删除掉list的最后一个元素，并打印这个元素<br>
* `pop(index)` : 删除掉位于索引号index位置的元素并打印这个元素<br>
* Note：list为有序集合，所包含的元素并不要求必须是同一种数据类型<br>

`str.join(item)` : 字符串操作函数
`','.join('abc')` 代表将字符串abc中的每个成员以字符','分隔开再拼接成一个字符串，输出为`'a,b,c'`
```
class Solution:
    def backspaceCompare(self, S: str, T: str) -> bool:
        def build(s: str) -> str:
            ret = list()
            for ch in s:
                if ch != "#":
                    ret.append(ch)
                elif ret:
                    ret.pop()
            return "".join(ret)
        
        return build(S) == build(T)
```
### **977:easy:有序数组的平方**
```
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        n = len(nums)
        ans = [0] * n 
        i, j, pos = 0, n-1, n-1
        
        while i <= j:
            if nums[i] * nums[i] > nums[j] * nums[j]:
                ans[pos] = nums[i] * nums[i]
                i += 1
            else:
                ans[pos] = nums[j] * nums[j]
                j -= 1
            pos -= 1
        
        return ans
```
