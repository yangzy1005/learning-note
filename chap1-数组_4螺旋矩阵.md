# chap1.数组

## 4.螺旋矩阵Ⅱ
* 循环不变量原则： 例如左闭右开（拐角处留给新一条边处理），如下图
![](/images/1.png)
### **59:medium:螺旋矩阵Ⅱ**
```
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        nums = [[0] * n for _ in range(n)]
        startx, starty = 0, 0
        loop, mid = n // 2, n // 2
        count = 1

        for offset in range(1, loop + 1):
            for i in range(starty, n - offset):
                nums[startx][i] = count
                count += 1
            for i in range(startx, n - offset):
                nums[i][n - offset] = count
                count += 1
            for i in range(n - offset, starty, -1):
                nums[n - offset][i] = count
                count += 1
            for i in range(n - offset, startx, -1):
                nums[i][starty] = count
                count += 1
            startx += 1
            starty += 1
        
        if n % 2 != 0:
            nums[mid][mid] = count
        return nums
```
### **54:medium:螺旋矩阵**
* 先把拐角坐标写出来：
![](/images/2.jpg)
```
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        m, n = len(matrix), len(matrix[0])
        startx, starty = 0, 0
        loop = m // 2 if m < n else n // 2
        nums=[0] * (m * n)
        count = 0
        for offset in range(loop):
            for i in range(starty, n - offset - 1):
                nums[count] = matrix[startx][i]
                count += 1
            for i in range(startx, m - offset - 1):
                nums[count] = matrix[i][n - offset - 1]
                count += 1
            for i in range(n - offset - 1, starty, -1):
                nums[count] = matrix[m - offset - 1][i]
                count += 1
            for i in range(m - offset - 1, startx, -1):
                nums[count] = matrix[i][starty]
                count += 1
            startx += 1
            starty += 1
        
        if m > n and n % 2 == 1:
            for i in range(m - n + 1):
                nums[count] = matrix[startx + i][starty]
                count += 1
        elif m < n and m % 2 == 1:
            for i in range(n - m + 1):
                nums[count] = matrix[startx][starty + i]
                count += 1

        return nums
```
### **剑指Offer 29:easy:顺时针打印矩阵**
```
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        if not matrix or not matrix[0]:
            return list()
        
        m, n = len(matrix), len(matrix[0])
        short = min(m, n)
        loop = short // 2
        startx, starty = 0, 0
        out = [0] * n * m
        count = 0
        for offset in range(loop):
            for i in range(starty, n - offset - 1):
                out[count] = matrix[startx][i]
                count += 1
            for i in range(startx, m - offset - 1):
                out[count] = matrix[i][n - offset - 1]
                count += 1
            for i in range(n - offset - 1, starty, -1):
                out[count] = matrix[m - offset - 1][i]
                count += 1
            for i in range(m - offset - 1, startx, -1):
                out[count] = matrix[i][starty]
                count += 1
            startx += 1
            starty += 1
        if short % 2 == 1:
            if m == short:
                for i in range(n - m + 1):
                    out[count] = matrix[startx][starty + i]
                    count += 1
            else:
                for i in range(m - n + 1):
                    out[count] = matrix[startx + i][starty]
                    count += 1
        return out
```