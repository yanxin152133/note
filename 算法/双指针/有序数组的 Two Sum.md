# 有序数组的 Two Sum
## 输入输出样例
```
输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
```
## 题目描述
给定一个已按照升序排列的有序数组，找到两个数使得它们相加之和等于目标数。
函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。
说明:
- 返回的下标值（index1 和 index2）不是从零开始的。
- 你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
## 思路
使用双指针，一个指针指向值较小的元素，一个指针指向值较大的元素。指向较小元素的指针从头向尾遍历，指向较大元素的指针从尾向头遍历。
- 如果两个指针指向元素的和sum==target，那么得到要求的结果；
- 如果sum>target,移动较大的元素，使sum变小一些；
- 如果sum<target，移动较小的元素，使sum变大一些。
## 示例代码
```
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        // 设置两个下标，一个从较小的位置开始遍历，一个从较大的位置开始遍历
        int i=0,j=numbers.length-1;
        // 使numbers中的两个开始相加，结果与target进行比较
        while(i<j){
            // 保存两个数相加之和
            int sum=numbers[i]+numbers[j];
            // 比较sum与target
            if(sum==target){    //如果相等，则返回一个数组，其中为下标值
                return new int[]{i+1,j+1};
            }
            // 当sum大于target时，将从较大值开始遍历的下标减小
            else if(sum>target){
                j--;
            }
            // 当sum小于target时，将从较小值开始遍历的下标增大
            else{
                i++;
            }
        }
        return null;
    }
}
```