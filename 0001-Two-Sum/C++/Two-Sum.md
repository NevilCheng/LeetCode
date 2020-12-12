## 暴力搜索算法

>解题思路：利用两个循环解决

> **代码**
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = nums.size();
        for(int i = 0; i < n - 1; i++){           //i要小于n-1，当i为倒数第二个数时，j=i+1，j为最后一个。故而i要小于n-1
            for(int j = i + 1; j < n; j++){       // j=i+1,内层循环开始的时候，j要赋初值为i后面一个数字。故而j=i+1
                if (nums[i] + nums[j] == target){
                    return{i,j};
                }
            }
        }
        return{};
    }    
};
                                    
```

> **结果and总结**
- 运行时间：12ms &emsp;&emsp;&emsp;&emsp; 内存消耗：9MB
- 时间复杂度：O(N^2)，其中 N 是数组中的元素数量。最坏情况下数组中任意两个数都要被匹配一次
- 空间复杂度：O(1)







