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



## 哈希表

> 解决思路：
- 注意到上一个方法的时间复杂度较高的原因是寻找 `target - x` 的时间复杂度过高。因此，我们需要一种更便捷的方法，能够快速寻找数组中是否存在目标元素。如果存在，我们需要找出它的索引。
- 使用哈希表，可以将寻找 `target - x` 的时间复杂度降低到从 O(N) 降低到 O(1)。
- 创建一个哈希表，对于每一个 x，我们首先查询哈希表中是否存在`target - x`，然后将 x 插入到哈希表中，可保证 x 不会和自己匹配。

> **代码**
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> hashtable;
        for(int i = 0; i < nums.size(); ++i){
            auto it = hashtable.find(target - nums[i]);
            if(it != hashtable.end()) {
                return {it->second, i};
            }
            hashtable[nums[i]] = i;
        }
        return {};
    }
};                                  
```

> **解析**
- unordered_map是一个关联容器，内部采用的是hash表结构，拥有快速检索的功能。通过key去检索value，而不是通过绝对地址;键唯一性：不存在两个元素的键一样.
- auto是根据后面的值，来自己推测前面的类型是什么。
- end()指向最后一个元素的下一个地址，(未解决)现猜想找到的it值，在hashtable中不存在后，返回两个数的地址。即target为8，num[i]为4，而找到的8-4=4也是




> **结果and总结**
- 运行时间：8ms &emsp;&emsp;&emsp;&emsp; 内存消耗：9.3MB
- 时间复杂度：O(N)，其中 N 是数组中的元素数量。对于每一个元素 x，我们可以 O(1) 地寻找 target - x。
- 空间复杂度：O(N), 其中 N 是数组中的元素数量。主要为哈希表的开销。



















