# 前K个高频元素

## 输入输出样例
### 示例一
```
输入：nums=[1,1,1,2,2,3],k=2
输出：[1,2]
```
### 示例二
```
输入：nums=[1],k=1
输出：[1]
```
说明：
- 你可以假设给定的k总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
- 你的算法的时间复杂度必须优于O(n log n) , n 是数组的大小。
## 题目描述
给定一个非空的整数数组，返回其中出现频率前k高的元素。
## 思路
设置若干个桶，每个桶存储出现频率相同的数。桶的下标表示数出现的频率，即第 i 个桶中存储的数出现的频率为 i。
把数都放到桶之后，从后向前遍历桶，最先得到的 k 个数就是出现频率最多的的 k 个数
## 代码示例
```
class  Solution {
     public   List < Integer > topKFrequent( int [] nums,  int  k) {
         List < Integer > res  =   new  ArrayList();
         // 使用字典，统计每个元素出现的次数，元素为键，元素出现的次数为值
         HashMap < Integer ,  Integer > map  =   new  HashMap();
         for  ( int  num  :  nums) {
             if  (map.containsKey(num)) {
                map.put(num, map.get(num)  +   1 );
            }  else  {
                map.put(num,  1 );
            }
        }


         // 桶排序
         // 将频率作为数组下标，对于出现频率不同的数字集合，存入对应的数组下标
         List < Integer >[] list  =   new   List [nums.length  +   1 ];
         for  ( int  key  :  map.keySet()) {
             // 获取出现的次数作为下标
             int  i  =  map.get(key);
             if  (list[i]  ==   null ) {
                list[i]  =   new  ArrayList();
            }
            list[i].add(key);
        }

         // 倒序遍历数组获取出现顺序从大到小的排列
         for  ( int  i  =  list.length  -   1 ; i  >=   0   &&  res.size()  <  k; i -- ) {
             if  (list[i]  ==   null )
                 continue ;
            res.addAll(list[i]);
        }
         return  res;
    }
}
```