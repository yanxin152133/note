# 数组中的第K个最大元素

## 输入输出样例
### 示例一
```
输入：[3,2,1,5,6,4]和k=2
输出：5
```
### 示例二
```
输入：[3,2,3,1,2,4,5,5,6]和k=4
输出：4
```
说明：你可以假设k总是有效的，且1≤ k ≤ 数组的长度。
## 题目描述
在未排序的数组中找到第k个最大的元素。请注意，你需要找的是数组排序后的第k个最大的元素，而不是第k个不同的元素。
## 思路
1. 排序。对数组进行排序，然后找到第K大的数
2. 堆
3. 快速选择
## 代码示例
1. 排序
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length-k];
    }
}
```
2. 堆
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(); // 小顶堆
        for (int val : nums) {
            pq.add(val);
            if (pq.size() > k)  // 维护堆的大小为 K
                pq.poll();
        }
        return pq.peek();
    }
}
```
3. 快速选择
```
class  Solution {
     public   int  findKthLargest( int [] nums,  int  k) {
        k  =  nums.length  -  k;
         int  l  =   0 , h  =  nums.length  -   1 ;
         while  (l  <  h) {
             int  j  =  partition(nums, l, h);
             if  (j  ==  k) {
                 break ;
            }  else   if  (j  <  k) {
                l  =  j  +   1 ;
            }  else  {
                h  =  j  -   1 ;
            }
        }
         return  nums[k];
    }


     private   int  partition( int [] a,  int  l,  int  h) {
         int  i  =  l, j  =  h  +   1 ;
         while  ( true ) {
             while  (a[ ++ i]  <  a[l]  &&  i  <  h)
                ;
             while  (a[ -- j]  >  a[l]  &&  j  >  l)
                ;
             if  (i  >=  j) {
                 break ;
            }
            swap(a, i, j);
        }
        swap(a, l, j);
         return  j;
    }

     private   void  swap( int [] a,  int  i,  int  j) {
         int  t  =  a[i];
        a[i]  =  a[j];
        a[j]  =  t;
    }
}


```