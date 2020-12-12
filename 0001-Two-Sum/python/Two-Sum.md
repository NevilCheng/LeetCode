## 暴力搜索算法

>解题思路：利用两个循环解决

> **代码**
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return[i,j]
        return[]
                                    
```  

> **结果and总结**
 
运行时间：6132ms &emsp;&emsp;&emsp;&emsp; 内存消耗：14MB

此处用到了两个循环

&nbsp;

## 利用python中list相关函数解决
#### 方法一：
> 解题思路：
找到<kbd>num2 == target - num1</kbd> 是否在<kbd>list</kbd>中，然后运用两个方法：
- <kbd>num2 in nums</kbd> 返回true说明成功
- <kbd>nums.index(num2)</kbd> 查找num2的索引

> **代码**

 ```python
 class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums):
            num1 = nums[i]
            num2 = target - num1
            if num2 in nums:
                #如果num2=num1，且在nums中出现了一次，说明找到num1本身。
                if(num1 == num2) & (nums.count(num2)==1): 
                    continue
                return[i,nums.index(num2,i+1)]  #index(num2,i+1)是从num1后的序列找num2位置
 ```
> **结果and总结**

运行时间：1148ms &emsp;&emsp;&emsp;&emsp; 内存消耗：14MB

此处用到了一个循环

&nbsp;

#### 方法二：
>解题思路：在方法一的基础上，<kbd>num2</kbd>的查找不需要每次从<kbd>nums</kbd>查找一遍，可以按照切片的思想从<kbd>num1</kbd>之前或者之后查找就行。这次从<kbd>num1</kbd>之前找：
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(1,len(nums)):
            temp = nums[:i]
            num1 = target - nums[i]
            if num1 in temp:
                j = temp.index(num1)
                return[j,i]        
```

> **结果and总结**
运行时间：408ms &emsp;&emsp;&emsp;&emsp; 内存消耗：13.8MB

这个算法先找到列表[2,7,11,15]中的7，再找到2；所以<kbd>return[j,i]</kbd>时先返回j,再返回i

&nbsp;


## 利用字典解决
#### 方法一：
>解题思路：利用字典模拟哈希求解，遍历列表同时查字典
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dct = {}
        for i, n in enumerate(nums):
            if target-n in dct:
                return [dct[target - n], i]  
            dct[n] = i              #构造字典
```

> **结果and总结**
运行时间：48ms &emsp;&emsp;&emsp;&emsp; 内存消耗：14.6MB

- 这个算法先用列表中的[2,7,11,15]，9-2=7在字典中查找7，但此时字典是空的，把2存入字典；
- 然后再用9-7=2在字典中查找，此时字典中已存入了一个2，找到了7和2的位置；
- 在返回时<kbd>return[dct[target - n],i]</kbd> ，此时target - n 为9-7=2，故先返回2的位置，再返回7的位置

&nbsp;

## 小结
利用字典解决该问题最简单，遍历列表同时查字典，但也消耗了一定内存






