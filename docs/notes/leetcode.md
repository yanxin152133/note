# 算法思想
>该笔记参考以下来源。
      
![](https://github.com/CyC2018/CS-Notes/raw/master/assets/LogoMakr_0zpEzN.png)
     
>详情请点击[链接](https://cyc2018.github.io/CS-Notes/#/)
       
## 二分查找
### 1. x的平方根
输入输出样例
- 示例一
       
```html
输入: 4
输出: 2
```
       
- 示例二
       
```html
输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 
     由于返回类型是整数，小数部分将被舍去。
```
       
题目描述          
实现 int sqrt(int x) 函数。
计算并返回 x 的平方根，其中 x 是非负整数。
由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
        
思路      
1. 首先一个数不会超过其一半的平方
2. 使用二分查找来缩小每次的范围
           
代码示例     
      
```java
class Solution {
    public int mySqrt(int x) {
    if (x <= 1) {
        return x;
    }
    int l = 1, h = x;
    while (l <= h) {
        int mid = l + (h - l) / 2;
        int sqrt = x / mid;
        if (sqrt == mid) {
            return mid;
        } else if (mid > sqrt) {
            h = mid - 1;
        } else {
            l = mid + 1;
        }
    }
    return h;
    }
}
```
        
### 2. 寻找比目标字母大的最小字母
输入输出样例
              
```html
输入:
letters = ["c", "f", "j"]
target = "a"
输出: "c"

输入:
letters = ["c", "f", "j"]
target = "c"
输出: "f"

输入:
letters = ["c", "f", "j"]
target = "d"
输出: "f"

输入:
letters = ["c", "f", "j"]
target = "g"
输出: "j"

输入:
letters = ["c", "f", "j"]
target = "j"
输出: "c"

输入:
letters = ["c", "f", "j"]
target = "k"
输出: "c"
```

注:
1. letters长度范围在[2, 10000]区间内。
2. letters 仅由小写字母组成，最少包含两个不同的字母。
3. 目标字母target 是一个小写字母。
             
题目描述         
给定一个只包含小写字母的有序数组letters 和一个目标字母 target，寻找有序数组里面比目标字母大的最小字母。        
数组里字母的顺序是循环的。举个例子，如果目标字母target = 'z' 并且有序数组为 letters = ['a', 'b']，则答案返回 'a'。      
           
代码示例
         
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        int n=letters.length;
        int i=0,j=n-1;
        while(i<=j){
            int mid=i+(j-i)/2;
            if(letters[mid]<=target){
                i=mid+1;
            }else{
                j=mid-1;
            }
        }
        return 1 < n ? letters[i] : letters[0];
    }
}
```

### 3. 有序数组中的单一元素
输入输出样例
- 示例一
       
```html
输入: [1,1,2,3,3,4,4,8,8]
输出: 2
```
       
- 示例二
       
```html
输入: [3,3,7,7,10,11,11]
输出: 10
```
        
**注意: 您的方案应该在 O(log n)时间复杂度和 O(1)空间复杂度中运行**
        
题目描述          
给定一个只包含整数的有序数组，每个元素都会出现两次，唯有一个数只会出现一次，找出这个数。
            
思路        
1. 出现一次的元素在奇数位上,同时需要保证mid为偶数
2. nums[mid]==nums[mind+1]，则使i=mid+2
3. nums[mid]!=nums[mid+1],则使j=mid
           
代码示例
             
```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int i=0,j=nums.length-1;
        while(i<j){
            int mid=i+(j-i)/2;
            if(mid%2==1){ //保证查找的位置在奇数位，在奇数位与m+1位的不同就表明m位置只出现一次
                mid--;
            }
            if(nums[mid]==nums[mid+1]){  
                i=mid+2;
            }else{
                j=mid;
            }
        }
        return nums[i];
    }
}
```
              
### 4. 第一个错误的版本
输入输出样例           
```html
给定 n = 5，并且 version = 4 是第一个错误的版本。
调用 isBadVersion(3) -> false
调用 isBadVersion(5) -> true
调用 isBadVersion(4) -> true
所以，4 是第一个错误的版本。 
```
             
题目描述            
你是产品经理，目前正在带领一个团队开发新的产品。不幸的是，你的产品的最新版本没有通过质量检测。由于每个版本都是基于之前的版本开发的，所以错误的版本之后的所有版本都是错的。                     
假设你有 n 个版本 [1, 2, ..., n]，你想找出导致之后所有版本出错的第一个错误的版本。               
你可以通过调用 bool isBadVersion(version) 接口来判断版本号 version 是否在单元测试中出错。实现一个函数来查找第一个错误的版本。你应该尽量减少对调用 API 的次数。          
             
思路             
1. 二分查找
          
代码示例
             
```java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int i=1,j=n;
        while(i<j){
            int mid=i+(j-i)/2;
            if(isBadVersion(mid)){
                j=mid;
            }else{
                i=mid+1;
            }
        }
        return i;
    }
}
```
           
### 5. 寻找旋转排序数组中的最小值
输入输出样例
- 示例一
       
```html
输入: [3,4,5,1,2]
输出: 1
```
       
- 示例二
       
```html
输入: [4,5,6,7,0,1,2]
输出: 0
```
       
题目描述                 
假设按照升序排序的数组在预先未知的某个点上进行了旋转。                
( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。              
请找出其中最小的元素。            
你可以假设数组中不存在重复元素。                 
               
思路               
1. 首先需要注意的是该数组的排序是被打乱的，因此需要考虑中间的值与那个值比较
2. 数组原本是升序，比如，如果中间位置的值与最后一个值比较，若小于，说明最小值在左边，若大于则在右边
              
代码示例
```java
class Solution {
    public int findMin(int[] nums) {
        int i=0,j=nums.length-1;
        while(i<j){
            int mid=i+(j-i)/2;
            if(nums[mid]<=nums[j]){
                j=mid;
            }else{
                i=mid+1;
            }
        }
        return nums[i];
    }
}
```
         
### 6. 在排序数组中查找元素的第一个和最后一个位置
输入输出样例
- 示例一
       
```html
输入: nums = [5,7,7,8,8,10], target = 8
输出: [3,4]
```
       
- 示例二
       
```html
输入: nums = [5,7,7,8,8,10], target = 6
输出: [-1,-1]
```
       
题目描述               
给定一个按照升序排列的整数数组nums，和一个目标值target。找出给定目标值在数组中的开始位置和结束位置。            
你的算法时间复杂度必须是O(log n)级别。            
如果数组中不存在目标值，返回[-1,-1]。            
              
思路            
1. 需要考虑数组中是否有相同的元素
2. 通过查找target+1的目标值，来确定区间的边界
3. 同时需要考虑只有一个元素的数组的情况
            
代码示例
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int first=binarySearch(nums,target);
        int last=binarySearch(nums,target+1)-1;//target+1是为了找比目标值大1的数，通过last来找到一个小于target的区间
        if(first==nums.length||nums[first]!=target){
            return new int[]{-1,-1};
        }else{
            return new int[]{first,last}; //可以判断first和last的大小来决定谁在前谁在后，防止结果出错
        }
        
    }
    private int binarySearch(int[] nums,int target){
        int i=0,j=nums.length; //j=nums.length需要注意，考虑如果数组中只有一个元素的情况
        while(i<j){
            int mid=i+(j-i)/2;
            if(nums[mid]>=target){
                j=mid;
            }else{
                i=mid+1;
            }
        }
        return i;
    }
}
```
     
## 排序
### 快速选择
用于求解 Kth Element 问题，也就是第 K 个元素的问题。            
可以使用快速排序的 partition() 进行实现。需要先打乱数组，否则最坏情况下时间复杂度为 O(N2)。        
               
### 堆
用于求解 TopK Elements 问题，也就是 K 个最小元素的问题。可以维护一个大小为 K 的最小堆，最小堆中的元素就是最小元素。最小堆需要使用大顶堆来实现，大顶堆表示堆顶元素是堆中最大元素。这是因为我们要得到 k 个最小的元素，因此当遍历到一个新的元素时，需要知道这个新元素是否比堆中最大的元素更小，更小的话就把堆中最大元素去除，并将新元素添加到堆中。所以我们需要很容易得到最大元素并移除最大元素，大顶堆就能很好满足这个要求。             
堆也可以用于求解 Kth Element 问题，得到了大小为 k 的最小堆之后，因为使用了大顶堆来实现，因此堆顶元素就是第 k 大的元素。                  
快速选择也可以求解 TopK Elements 问题，因为找到 Kth Element 之后，再遍历一次数组，所有小于等于 Kth Element 的元素都是 TopK Elements。          
可以看到，快速选择和堆排序都可以求解 Kth Element 和 TopK Elements 问题。          
              
### 1. 数组中的第K个最大元素
输入输出样例
- 示例一
```html
输入：[3,2,1,5,6,4]和k=2
输出：5
```
          
- 示例二
```html
输入：[3,2,3,1,2,4,5,5,6]和k=4
输出：4
```
        
说明：你可以假设k总是有效的，且1≤ k ≤ 数组的长度。
题目描述      
在未排序的数组中找到第k个最大的元素。请注意，你需要找的是数组排序后的第k个最大的元素，而不是第k个不同的元素。
                
思路      
1. 排序。对数组进行排序，然后找到第K大的数
2. 堆
3. 快速选择
              
代码示例      
1. 排序            
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        Arrays.sort(nums);
        return nums[nums.length-k];
    }
}
```
             
2. 堆
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(); // 小顶堆
        for (int val : nums) {
            pq.add(val);
            if (pq.size() > k) // 维护堆的大小为 K
                pq.poll();
        }
        return pq.peek();
    }
}
```
             
3. 快速选择              
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        k = nums.length - k;
        int l = 0, h = nums.length - 1;
        while (l < h) {
            int j = partition(nums, l, h);
            if (j == k) {
                break;
            } else if (j < k) {
                l = j + 1;
            } else {
                h = j - 1;
            }
        }
        return nums[k];
    }

    private int partition(int[] a, int l, int h) {
        int i = l, j = h + 1;
        while (true) {
            while (a[++i] < a[l] && i < h)
                ;
            while (a[--j] > a[l] && j > l)
                ;
            if (i >= j) {
                break;
            }
            swap(a, i, j);
        }
        swap(a, l, j);
        return j;
    }

    private void swap(int[] a, int i, int j) {
        int t = a[i];
        a[i] = a[j];
        a[j] = t;
    }
}
```
                  
### 2. 前K个高频元素
输入输出样例
- 示例一
```html
输入：nums=[1,1,1,2,2,3],k=2
输出：[1,2]
```
          
- 示例二
```html
输入：nums=[1],k=1
输出：[1]
```
        
说明：
- 你可以假设给定的k总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
- 你的算法的时间复杂度必须优于O(n log n) , n 是数组的大小。
            
题目描述          
给定一个非空的整数数组，返回其中出现频率前k高的元素。
           
思路      
设置若干个桶，每个桶存储出现频率相同的数。桶的下标表示数出现的频率，即第 i 个桶中存储的数出现的频率为 i。             
把数都放到桶之后，从后向前遍历桶，最先得到的 k 个数就是出现频率最多的的 k 个数
                   
代码示例           
```java
class Solution {
    public List<Integer> topKFrequent(int[] nums, int k) {
        List<Integer> res = new ArrayList();
        // 使用字典，统计每个元素出现的次数，元素为键，元素出现的次数为值
        HashMap<Integer, Integer> map = new HashMap();
        for (int num : nums) {
            if (map.containsKey(num)) {
                map.put(num, map.get(num) + 1);
            } else {
                map.put(num, 1);
            }
        }

        // 桶排序
        // 将频率作为数组下标，对于出现频率不同的数字集合，存入对应的数组下标
        List<Integer>[] list = new List[nums.length + 1];
        for (int key : map.keySet()) {
            // 获取出现的次数作为下标
            int i = map.get(key);
            if (list[i] == null) {
                list[i] = new ArrayList();
            }
            list[i].add(key);
        }

        // 倒序遍历数组获取出现顺序从大到小的排列
        for (int i = list.length - 1; i >= 0 && res.size() < k; i--) {
            if (list[i] == null)
                continue;
            res.addAll(list[i]);
        }
        return res;
    }
}
```
                  
### 3. 根据字符出现频率排序
输入输出样例
- 示例一
```html
输入：
"tree"
输出：
"eert"
解释：
'e'出现两次，'r'和't'都只出现一次。
因此'e'必须出现在'r'和't'之前。此外，'eetr'也是一个有效的答案。
```
          
- 示例二
```html
输入：
"cccaaa"
输出：
"cccaaa"
解释：
'c'和'a'都出现三次。此外，"aaaccc"也是有效的答案。
注意"cacaca"是不正确的，因为相同的字母必须放在一起。
```
          
- 示例三
```html
输入：
"Aabb"
输出：
"bbAa"
解释：
此外，"bbaA"也是一个有效的答案，但"Aabb"是不正确的。
注意'A'和'a'被认为是两种不同的字符。
```
              
题目描述          
给定一个字符串，请将字符串里的字符按照出现的频率降序排列。
             
思路          
- 遍历字符数组，将每个字符的和它对应的频次存入哈希表中。
- 新建一个桶，将每个字符存入索引为它的频次的那个桶中。由于桶的索引本身就是自增的，因此这样就直接利用桶完成了对每个字符按照它的出现次数进行了从大到小的排序。
- 倒着遍历桶，将每个桶里的元素取出来，并按照它的频次存入要返回的结果中。
             
代码示例           
```java
class Solution {
    public String frequencySort(String s) {
        Map<Character, Integer> frequencyForNum = new HashMap<>();
        for (char c : s.toCharArray())
            frequencyForNum.put(c, frequencyForNum.getOrDefault(c, 0) + 1);

        List<Character>[] frequencyBucket = new ArrayList[s.length() + 1];
        for (char c : frequencyForNum.keySet()) {
            int f = frequencyForNum.get(c);
            if (frequencyBucket[f] == null) {
                frequencyBucket[f] = new ArrayList<>();
            }
            frequencyBucket[f].add(c);
        }
        StringBuilder str = new StringBuilder();
        for (int i = frequencyBucket.length - 1; i >= 0; i--) {
            if (frequencyBucket[i] == null) {
                continue;
            }
            for (char c : frequencyBucket[i]) {
                for (int j = 0; j < i; j++) {
                    str.append(c);
                }
            }
        }
        return str.toString();
    }
}
```
               
### 4. 荷兰国旗问题
>荷兰国旗包含三种颜色：红、白、蓝。
>有三种颜色的球，算法的目标是将这三种球按颜色顺序正确地排列。它其实是三向切分快速排序的一种变种，在三向切分快速排序中，每次切分都将数组分成三个区间：小于切分元素、等于切分元素、大于切分元素，而该算法是将数组分成三个区间：等于红色、等于白色、等于蓝色。
         
![](https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/7a3215ec-6fb7-4935-8b0d-cb408208f7cb.png)
          
输入输出样例
- 示例一
```html
输入：[2,0,2,1,1,0]
输出：[0,0,1,1,2,2]
```
        
题目描述          
给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。      
此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色       
**注意:**       
不能使用代码库中的排序函数来解决这道题。     
                      
代码示例           
```java
class Solution {
    public void sortColors(int[] nums) {
        int zero = -1, one = 0, two = nums.length;
        while (one < two) {
            if (nums[one] == 0) {
                swap(nums, ++zero, one++);
            } else if (nums[one] == 2) {
                swap(nums, --two, one);
            } else {
                ++one;
            }
        }
    }

    private void swap(int[] nums, int i, int j) {
        int t = nums[i];
        nums[i] = nums[j];
        nums[j] = t;
    }
}
```
               
## 双指针
### 1. 两数平方和
输入输出样例
- 示例一
```html
输入：5
输出：True
解释：1*1+2*2=5
```
          
- 示例二
```html
输入：3
输出：False
```
           
题目描述             
给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c。
           
思路         
- a2 + b2 = c==》a2 + b2 = r2。其中r2=c,可以通过求c的平方根。以此来缩小范围；
- 之后进行比较。
            
代码示例            
```java
class Solution {
    public boolean judgeSquareSum(int c) {
        int i=0,j=(int)Math.sqrt(c); //求平方根来缩小范围
        while(i<=j){
            // 通过result来保存两数平方之和
            int result=i*i+j*j;
            if(result==c){
                return true;
            }
            else if(result<c){
                i++;
            }
            else{
                j--;
            }
        }
        return false;
    }
}
```
             
### 2. 反转字符串中的元音字母
输入输出样例
- 示例一
```html
输入："hello"
输出："holle"
```
          
- 示例二
```html
输入："leetcode"
输出："leotcede"
```

说明：元音子没有不包含字母“y”
          
题目描述             
编写一个函数，以字符串作为输入，反转该字符串中的元音子母。
           
思路          
使用双指针指向带反转的两个元音字符，一个指针从头向尾遍历，一个指针从尾到头遍历。
               
代码示例            
```java
class Solution {
    private final static HashSet<Character> vowels = new HashSet<>(Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));
    public String reverseVowels(String s) {
         // 设置下标，一个从头向尾遍历，一个从尾向头遍历
        int i=0,j=s.length()-1;
        // 新增一个数组来保存替换之后的新数组
        char[] result=new char[s.length()];
        while(i<=j){
            // 获取当前指针指向的值
            char ci=s.charAt(i);
            char cj=s.charAt(j);
            if(!vowels.contains(ci)){ // 不包含元音字母，则继续遍历
                result[i++]=ci;
            }
            else if(!vowels.contains(cj)){
                result[j--]=cj;
            }
            else{ // 包含元音字母，则交换
                result[i++]=cj;
                result[j--]=ci;
            }
        }
        return new String(result);
    }
}
```
         
### 3. 有序数组的Two Sum
输入输出样例
- 示例一
```html
输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
```
                   
题目描述             
给定一个已按照升序排列的有序数组，找到两个数使得它们相加之和等于目标数。           
函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。
               
说明:
- 返回的下标值（index1 和 index2）不是从零开始的。
- 你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
                   
思路          
使用双指针，一个指针指向值较小的元素，一个指针指向值较大的元素。指向较小元素的指针从头向尾遍历，指向较大元素的指针从尾向头遍历。             
- 如果两个指针指向元素的和sum==target，那么得到要求的结果；
- 如果sum>target,移动较大的元素，使sum变小一些；
- 如果sum<target，移动较小的元素，使sum变大一些。
               
代码示例            
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        // 设置两个下标，一个从较小的位置开始遍历，一个从较大的位置开始遍历
        int i=0,j=numbers.length-1;
        // 使numbers中的两个开始相加，结果与target进行比较
        while(i<j){
            // 保存两个数相加之和
            int sum=numbers[i]+numbers[j];
            // 比较sum与target
            if(sum==target){ //如果相等，则返回一个数组，其中为下标值
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
             
### 4. 验证回文字符串||
输入输出样例
- 示例一
```html
输入："abc"
输出：True
```
          
- 示例二
```html
输入：
输出：
解释：你可以删除c字符
```

注意：字符串只包含从a-z的小写子没有。字符串的最大长度为50000。
             
题目描述            
给定一个非空字符串s，最多删除一个字符。判断是否能成为回文字符串。（“回文串”是一个正读和反读都一样的字符串，比如“level”或者“noon”等等就是回文串。）
               
思路     
1. 先循环遍历字符串，一个从头到尾开始，一个从尾到头开始
2. 然后进行比较，如果遇到两个不相等的时候，就将两个中的一个进行排序，不去考虑。
3. 由于只能最多删除一个字符，所以只需要对排除后的字符串再次循环遍历，并进行比较。能成为回文字符串则返回true，否则返回false。
                 
代码示例            
```java
class Solution {
    public boolean validPalindrome(String s) {
        // 先循环遍历
        for(int i=0,j=s.length()-1;i<j;i++,j--){
            if(s.charAt(i)!=s.charAt(j)){  
                return isPalindrome(s,i+1,j)||isPalindrome(s,i,j-1);
            }
        }
        return true;
    }
    private boolean isPalindrome(String s,int i,int j){
        while(i<j){
            if(s.charAt(i++)!=s.charAt(j--)){
                return false;
            }
        }
        return true;
    }
}
```
             
### 5. 合并两个有序数组
输入输出样例
- 示例一
```html
输入：
nums1=[1,2,3,0,0,0],m=3
nums2=[2,5,6],      n=3
输出：[1,2,2,3,5,6]
```
                     
题目描述             
给定两个有序整数数组nums1和nums2，将nums2合并到nums1中，使得nums1成为一个有序数组。               
说明：
- 初始化nums1和nums2的元素数量分别为m和n
- 你可以假设nums1有足够的空间（空间大小大于或等于m+n）来保存nums2中的元素。
                
思路          
- 从尾开始遍历
- index1从nums1开始，index2从nums2开始，index3则是合并后数组长度
- nums2[index2]>nums1[index1]时，则将num2[index2]放置于nums1[index3]位置上，然后index2--,index3--;此时index1没有发生改变
- nums2[index1]<nums1[index1]时，则将nums1[index1]放置于nums1[index3]位置上，然后index1--,index3--;此时index2没有发生改变
- 同时需要考虑index1、index2小于0的情况
            
代码示例            
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int index1=m-1;   
        int index2=n-1;
        int index3=m+n-1;
        while(index1>=0||index2>=0){
            if(index1<0){
                nums1[index3--]=nums2[index2--];
            }
            else if(index2<0){
                nums1[index3--]=nums1[index1--];
            }
            else if(nums1[index1]>nums2[index2]){
                nums1[index3--]=nums1[index1--];
            }else{
                nums1[index3--]=nums2[index2--];
            }
        }
    }
}
```
             
### 6. 通过删除字母匹配到字典里最长单词
输入输出样例
- 示例一
```html
输入：
s = "abpcplea", d = ["ale","apple","monkey","plea"]
输出：
"apple"
```
          
- 示例二
```html
输入：
s = "abpcplea", d = ["a","b","c"]
输出：
"a"
```

说明：         
1. 所有输入的字符串只包含小写字母
2. 字典的大小不会超过1000
3. 所有输入的字符串长度不会超过1000
              
题目描述     
给定一个字符串和一个字符串字典。找到字典里面最长的字符串，该字符串可以通过删除给定字符串的某些字符来得到。如果答案不止一个，返回长度最长且字典顺序最小的字符串。如果答案不存在，则返回空字符串。
                    
思路          
通过删除字符串 s 中的一个字符能得到字符串 t，可以认为 t 是 s 的子序列，我们可以使用双指针来判断一个字符串是否为另一个字符串的子序列。
             
代码示例            
```java
class Solution {
    public String findLongestWord(String s, List<String> d) {
        String longestWord="";
        for(String target:d){
            int l1=longestWord.length(),l2=target.length();
            if(l1>l2||(l1==l2&&longestWord.compareTo(target)<0)){
                continue;
            }
            if(isSubstr(s,target)){
                longestWord=target;
            }
        }
        return longestWord;
    }
    private boolean isSubstr(String s,String target){
        int i=0,j=0;
        while(i<s.length()&&j<target.length()){
            if(s.charAt(i)==target.charAt(j)){
                j++;
            }
            i++;
        }
        return j==target.length();
    }
}
```
             
### 7. 环形链表
输入输出样例
- 示例一
```html
输入：head=[3,2,0,-4],pos=1
输出：true
解释：链中有一个环，其尾部连接到第二个节点
```
              
![](https://live.staticflickr.com/65535/48736997907_be93d33478.jpg)
            
- 示例二
```html
输入：head=[1,2],pos=0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点
```
                
![](https://live.staticflickr.com/65535/48736493853_4e64650203_m.jpg)
               
- 示例三
```html
输入：head=[1],pos=-1
输出：false
解释：链表中没有环
```
                 
![](https://live.staticflickr.com/65535/48736493728_ca29a30277_t.jpg)
             
题目描述         
给定一个链表，判断链表中是否有环。         
为了表示给定链表中的环，我们使用整数pos来表示链尾连接到链表中的位置（索引从0开始）。如果pos是-1，则在该链表中没有环。   
             
思路    
- 使用双指针，一个指针每次移动一个节点，一个指针每次移动两个节点，如果存在环，那么这两个指针一定会相遇。
                
代码示例            
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 * int val;
 * ListNode next;
 * ListNode(int x) {
 * val = x;
 * next = null;
 * }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head==null){
            return false;
        }
        ListNode L1=head,L2=head.next;
        while(L1!=null&&L2!=null&&L2.next!=null){
            if(L1==L2){
                return true;
            }
            L1=L1.next;
            L2=L2.next.next;
        }
        return false;
    }
}
```
 
## 贪心思想
>保证每次操作都是局部最优的，并且最后得到的结果是全局最优的。
           
### 1. 分发饼干
输入输出样例
- 示例一
```html
输入: [1,2,3], [1,1]
输出: 1
解释: 
你有三个孩子和两块小饼干，3个孩子的胃口值分别是：1,2,3。
虽然你有两块小饼干，由于他们的尺寸都是1，你只能让胃口值是1的孩子满足。
所以你应该输出1。
```
        
- 示例二
```html
输入: [1,2], [1,2,3]
输出: 2
解释: 
你有两个孩子和三块小饼干，2个孩子的胃口值分别是1,2。
你拥有的饼干数量和尺寸都足以让所有孩子满足。
所以你应该输出2.
```
          
题目描述      
假设你是一位很棒的家长，想要给你的孩子们一些小饼干。但是，每个孩子最多只能给一块饼干。对每个孩子 i ，都有一个胃口值 gi ，这是能让孩子们满足胃口的饼干的最小尺寸；并且每块饼干 j ，都有一个尺寸 sj 。如果 sj >= gi ，我们可以将这个饼干 j 分配给孩子 i ，这个孩子会得到满足。你的目标是尽可能满足越多数量的孩子，并输出这个最大数值。

**注意：**     
你可以假设胃口值为正。      
一个小朋友最多只能拥有一块饼干。       
                 
代码示例           
```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int i=0,j=0;
        while(i<g.length&&j<s.length){
            if(g[i]<=s[j]){
                i++;
            }
            j++;
        }
        return i;
    }
}
```
              
### 2. 无重叠区间
输入输出样例
- 示例一
```html
输入: [ [1,2], [2,3], [3,4], [1,3] ]
输出: 1
解释: 移除 [1,3] 后，剩下的区间没有重叠。
```
        
- 示例二
```html
输入: [ [1,2], [1,2], [1,2] ]
输出: 2
解释: 你需要移除两个 [1,2] 来使剩下的区间没有重叠。
```
          
- 示例三
```html
输入: [ [1,2], [2,3] ]
输出: 0
解释: 你不需要移除任何区间，因为它们已经是无重叠的了。
```
          
题目描述         
给定一个区间的集合，找到需要移除区间的最小数量，使剩余区间互不重叠。
           
注意:      
可以认为区间的终点总是大于它的起点。      
区间 [1,2] 和 [2,3] 的边界相互“接触”，但没有相互重叠。      
         
思路      
先计算最多能组成的不重叠区间个数，然后用区间总个数减去不重叠区间的个数。        
在每次选择中，区间的结尾最为重要，选择的区间结尾越小，留给后面的区间的空间越大，那么后面能够选择的区间个数也就越大。
按区间的结尾进行排序，每次选择结尾最小，并且和前一个区间不重叠的区间。          
             
代码示例           
```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        // 如果集合为空，则返回0
        if (intervals.length == 0) {
            return 0;
        }
        // 以区间的结尾进行排序
        Arrays.sort(intervals, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[1] - o2[1];    // 1代表以结尾排序，0代表以开头排序
            }
        });
        int num=1; //不重复区间的数量
        int end=intervals[0][1];
        for(int i=1;i<intervals.length;i++){
            if(intervals[i][0]<end){
                continue;
            }
            end=intervals[i][1];
            num++;
        }
        return intervals.length-num;

    }
}
```
              
### 3. 用最少数量的箭引爆气球
输入输出样例
- 示例一
```html
输入:
[[10,16], [2,8], [1,6], [7,12]]
输出:
2
解释:
对于该样例，我们可以在x = 6（射爆[2,8],[1,6]两个气球）和 x = 11（射爆另外两个气球）。
```
                  
题目描述         
在二维空间中有许多球形的气球。对于每个气球，提供的输入是水平方向上，气球直径的开始和结束坐标。由于它是水平的，所以y坐标并不重要，因此只要知道开始和结束的x坐标就足够了。开始坐标总是小于结束坐标。平面内最多存在104个气球。           
一支弓箭可以沿着x轴从不同点完全垂直地射出。在坐标x处射出一支箭，若有一个气球的直径的开始和结束坐标为 xstart，xend， 且满足 xstart ≤ x ≤ xend，则该气球会被引爆。可以射出的弓箭的数量没有限制。 弓箭一旦被射出之后，可以无限地前进。我们想找到使得所有气球全部被引爆，所需的弓箭的最小数量。
              
思路      
该题计算的是区间的重叠区间。[1,2][2,3]是重叠区间。
               
代码示例           
```java
class Solution {
    public int findMinArrowShots(int[][] points) {
        // 首先考虑points是否为空
        if(points.length==0){
            return 0;
        }
        //进行排序，以结尾进行升序排序
        Arrays.sort(points,new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o1[1] - o2[1];
            }
        });
        int num=1;
        int end=points[0][1];
        for(int i=1;i<points.length;i++){
            if(points[i][0]<=end){
                continue;
            }
            end=points[i][1];
            num++;
        }
        return num;
    }
}
```
              
### 4. 根据身高重建队列
输入输出样例
- 示例一
```html
输入:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]
输出:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]
```
           
题目描述         
假设有打乱顺序的一群人站成一个队列。 每个人由一个整数对(h, k)表示，其中h是这个人的身高，k是排在这个人前面且身高大于或等于h的人数。 编写一个算法来重建这个队列。
           
**注意：**          
总人数少于1100人。
            
思路           
为了使插入操作不影响后续的操作，身高较高的学生应该先做插入操作，否则身高较小的学生原先正确插入的第 k 个位置可能会变成第 k+1 个位置。
身高 h 降序、个数 k 值升序，然后将某个学生插入队列的第 k 个位置中。
             
![](../pict/2291135-73c3568d9278fb4f.gif)
             
代码示例           
```java
class Solution {
    public int[][] reconstructQueue(int[][] people) {
        // 首先判断是否为空
        if (people.length == 0) {
            return new int[0][0];
        }
        // 排序，身高降序，人数升序
        Arrays.sort(people, new Comparator<int[]>() {
            @Override
            public int compare(int[] a1, int[] a2) {
                if (a1[0] == a2[0]) {
                    return a1[1] - a2[1];
                } else {
                    return a2[0] - a1[0];
                }
            }
        });
        List<int[]> queue = new ArrayList<>();
        for (int[] p : people) {
            queue.add(p[1], p);
        }
        return queue.toArray(new int[queue.size()][]);
    }
}
```
              
### 5. 买股票的最佳时机
输入输出样例
- 示例一
```html
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。
```
        
- 示例二
```html
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```
          
题目描述         
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。             
如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。
注意你不能在买入股票前卖出股票。
           
思路       
1. 记录当前最小值
2. 与后面的值相减，求最大值
             
代码示例           
```java
class Solution {
    public int maxProfit(int[] prices) {
        int n=prices.length;
        if(n==0){
            return 0;
        }
        int min=prices[0];
        int max=0;
        for(int i=0;i<n;i++){
            if(min>prices[i]){
                min=prices[i];
            }else{
                max=Math.max(max,prices[i]-min);
            }
        }
        return max;
    }
}
```
              
### 6. 买股票的最佳时机||
输入输出样例
- 示例一
```html
输入: [7,1,5,3,6,4]
输出: 7
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 3 天（股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。
     随后，在第 4 天（股票价格 = 3）的时候买入，在第 5 天（股票价格 = 6）的时候卖出, 这笔交易所能获得利润 = 6-3 = 3 。
```
        
- 示例二
```html
输入: [1,2,3,4,5]
输出: 4
解释: 在第 1 天（股票价格 = 1）的时候买入，在第 5 天 （股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。
     注意你不能在第 1 天和第 2 天接连购买股票，之后再将它们卖出。
     因为这样属于同时参与了多笔交易，你必须在再次购买前出售掉之前的股票。
```
          
- 示例三
```html
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
```
            
题目描述         
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。           
设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。         
注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。        
           
思路        
对于 [a, b, c, d]，如果有 a <= b <= c <= d ，那么最大收益为 d - a。而 d - a = (d - c) + (c - b) + (b - a) ，因此当访问到一个 prices[i] 且 prices[i] - prices[i-1] > 0，那么就把 prices[i] - prices[i-1] 添加到收益中。
             
代码示例           
```java
class Solution {
    public int maxProfit(int[] prices) {
        int max=0;
        for(int i=1;i<prices.length;i++){   //注意i=1
            if(prices[i]>prices[i-1]){
                max+=(prices[i]-prices[i-1]);
            }
        }
        return max;
    }
}
```
              
### 7. 种花问题
输入输出样例
- 示例一
```html
输入: flowerbed = [1,0,0,0,1], n = 1
输出: True
```
        
- 示例二
```html
输入: flowerbed = [1,0,0,0,1], n = 2
输出: False
```

注意:          
1. 数组内已种好的花不会违反种植规则。
2. 输入的数组长度范围为 [1, 20000]。
3. n 是非负整数，且不会超过输入数组的大小。
               
题目描述         
假设你有一个很长的花坛，一部分地块种植了花，另一部分却没有。可是，花卉不能种植在相邻的地块上，它们会争夺水源，两者都会死去。          
给定一个花坛（表示为一个数组包含0和1，其中0表示没种植花，1表示种植了花），和一个数 n 。能否在不打破种植规则的情况下种入 n 朵花？能则返回True，不能则返回False。          
                
思路           
1. 遍历
2. 如果是1，则结束此次循环
3. 如果是0，则判断前后是否为0
              
代码示例           
```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int len=flowerbed.length;
        int count=0;
        for(int i=0;i<len&&count<n;i++){
            if(flowerbed[i]==1){
                continue;
            }
            // 判断是否只有一个花坛             
            int pre=i==0?0:flowerbed[i-1];
            int next=i==len-1?0:flowerbed[i+1];
            if(pre==0&&next==0){
                count++;
                flowerbed[i]=1;
            }
        }
        return count>=n;
    }
}
```
              
### 8. 判断子序列
输入输出样例
- 示例一
```html
输入：s="abc",t="ahbgdc"
输出：true
```
        
- 示例二
```html
输入：s="axc",t="ahbgdc"
输出：false
```
          
题目描述      
给定字符串 s 和 t ，判断 s 是否为 t 的子序列。                    
你可以认为 s 和 t 中仅包含英文小写字母。字符串 t 可能会很长（长度 ~= 500,000），而 s 是个短字符串（长度 <=100）。
字符串的一个子序列是原始字符串删除一些（也可以不删除）字符而不改变剩余字符相对位置形成的新字符串。（例如，"ace"是"abcde"的一个子序列，而"aec"不是。）
                  
代码示例           
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int index=-1;
        for(char c:s.toCharArray()){ //将字符串转化为数组
            index=t.indexOf(c,index+1); //找出c在t中第一次出现的位置，如果出现过，则从下一个位置找下一个字符
            if(index==-1){
                return false;
            }
        }
        return true;
            
    }
}
```
              
### 9. 非递减数列
输入输出样例
- 示例一
```html
输入: [4,2,3]
输出: True
解释: 你可以通过把第一个4变成1来使得它成为一个非递减数列。
```
        
- 示例二
```html
输入: [4,2,1]
输出: False
解释: 你不能在只改变一个元素的情况下将其变为非递减数列。
```
          
题目描述         
给定一个长度为 n 的整数数组，你的任务是判断在最多改变 1 个元素的情况下，该数组能否变成一个非递减数列。        
我们是这样定义一个非递减数列的： 对于数组中所有的 i (1 <= i < n)，满足 array[i] <= array[i + 1]。       
             
思路        
1. 从前往后开始遍历，初始时，i=1,如果nums[i-1]>nums[i]，由于要将数组改为非递减数组，所以可以使nums[i-1]变小，也就是nums[i-1]=nums[i]。
2. 同时当nums[i-2]>nums[i]时，需要使nums[i]=nums[i-1]，将nums[i]变大。
              
代码示例           
```java
class Solution {
    public boolean checkPossibility(int[] nums) {
        int count=0;
        for(int i=1;i<nums.length&&count<2;i++){
            if(nums[i]>=nums[i-1]){
                continue;
            }
            count++;
            if(i-2>=0&&nums[i-2]>nums[i]){
                nums[i]=nums[i-1]; //nums[i-2]>nums[i]时，nums[i-1]>nums[i],所以只能是nums[i]=nums[i-1]
            }else{
                nums[i-1]=nums[i];
            }
        }
        return count<=1;
    }
}
```
              
### 10. 最大字序和
输入输出样例
- 示例一
```html
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```
                 
题目描述         
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
         
思路       
1. sun为连续子数组之和，ans为输出结果
2. 如果 sum > 0，则说明 sum 对结果有增益效果，则 sum 保留并加上当前遍历数字
3. 如果 sum <= 0，则说明 sum 对结果无增益效果，需要舍弃，则 sum 直接更新为当前遍历数字
4. 每次比较 sum 和 ans的大小，将最大值置为ans，遍历结束返回结果
             
代码示例           
```java
class Solution {
    public int maxSubArray(int[] nums) {
        //判断nums是否为空
        if(nums.length==0){
            return 0;
        }
        
        int start=nums[0];
        int sum=start;
        
        for(int i=1;i<nums.length;i++){
            if(start>0){ //如果start大于0，则加上下一个数
                start=start+nums[i];
            }else{ //否则，将start改为下一个数
                start=nums[i];
            }
            sum=Math.max(sum,start); //找出最大值
        }
        return sum;
    }
}
```
            
### 11. 划分字母区间
输入输出样例
- 示例一
```html
输入: S = "ababcbacadefegdehijhklij"
输出: [9,7,8]
解释:
划分结果为 "ababcbaca", "defegde", "hijhklij"。
每个字母最多出现在一个片段中。
像 "ababcbacadefegde", "hijhklij" 的划分是错误的，因为划分的片段数较少。
```
           
注意:
1. S的长度在[1, 500]之间。
2. S只包含小写字母'a'到'z'。
           
题目描述      
字符串 S 由小写字母组成。我们要把这个字符串划分为尽可能多的片段，同一个字母只会出现在其中的一个片段。返回一个表示每个字符串片段的长度的列表。
            
思路      
1. 首先遍历，将每个字符出现的最后的位置保存在一个事先准备好的数组中
2. 创建一个list用来保存每个字母最多出现在一个片段中的长度，同时创建两个变量，一个为左端点preIndex，一个为右端点MaxIndex，同时还有一个变量index使其等于上一步中存储每个字符最后出现的位置的值
3. 通过MaxIndex与index比较，来确定右端点的位置
4. 之后将MaxIndex的值赋给preIndex。
5. 同时也需要preIndex的初始值，会影响计算list的长度的大小     
            
代码示例           
```java
class Solution {
    public List<Integer> partitionLabels(String S) {
        // 存放每个字母最后一次出现在字符串中的位置
        int[] last=new int[50];
        for(int i=0;i<S.length();i++){
            last[S.charAt(i)-'a']=i; // S.charAt(i)-'a'：两个字符相减实际上是ASCII码对应的数相减;
        }
        
        List<Integer> list=new ArrayList<>();
        int preIndex=-1,maxIndex=0; //preIndex表示上个区间的右端点，maxIndex表示当前遍历的字符最后出现位置的最大值
        for(int i=0;i<S.length();i++){
            int index=last[S.charAt(i)-'a'];
            
            // 更新区间的右端点，向右延展
            if(index>maxIndex){
                maxIndex=index;
            }
            
            //如果当前位置i等于当前所遍历的字符最后出现位置的最大值
            //说明maxIndex即为区间的右端点
            if(i==maxIndex){
                //添加区间的长度
                list.add(maxIndex-preIndex);
                preIndex=maxIndex;
            }
        }
        return list;
    }
}
```
              
## 分治
### 1. 为运算表达式设计优先级
输入输出样例          
- 示例一
```html
输入: "2-1-1"
输出: [0, 2]
解释: 
((2-1)-1) = 0 
(2-(1-1)) = 2
```
          
- 示例二
```html
输入: "2*3-4*5"
输出: [-34, -14, -10, -10, 10]
解释: 
(2*(3-(4*5))) = -34 
((2*3)-(4*5)) = -14 
((2*(3-4))*5) = -10 
(2*((3-4)*5)) = -10 
(((2*3)-4)*5) = 10
```
          
题目描述      
给定一个含有数字和运算符的字符串，为表达式添加括号，改变其运算优先级以求出不同的结果。你需要给出所有可能的组合的结果。有效的运算符号包含+，-以及*。
                 
思路        
1. 分解成容易解决的子问题，也就是按照运算符分成左右两部分，分别计算后，利用分隔符进行合并。
2. 如果没有运算符，就返回其本身。
         
代码示例          
```java
class Solution {
    public List<Integer> diffWaysToCompute(String input) {
        List<Integer> ways=new ArrayList<>();
        for(int i=0;i<input.length();i++){
            char c=input.charAt(i);
            if(c=='+'||c=='-'||c=='*'){
                List<Integer> left=diffWaysToCompute(input.substring(0,i));
                List<Integer> right=diffWaysToCompute(input.substring(i+1));
                for(int l:left){
                    for(int r:right){
                        switch(c){
                            case '+':
                                ways.add(l+r);
                                break;
                            case '-':
                                ways.add(l-r);
                                break;
                            case '*':
                                ways.add(l*r);
                                break;
                        }
                    }
                }
            }
        }
        if(ways.size()==0){
            ways.add(Integer.valueOf(input));
        }
        return ways;
    }
}
```
               
### 2. 不同的二叉搜索树||
输入输出样例          
- 示例一
```html
输入: 3
输出:
[
  [1,null,3,2],
  [3,2,null,1],
  [3,1,null,null,2],
  [2,1,3],
  [1,null,2,null,3]
]
解释:
以上的输出对应以下 5 种不同结构的二叉搜索树：

   1 3 3 2 1
    \ / / / \ \
     3 2 1 1 3 2
    / / \ \
   2 1 2 3
```
               
题目描述           
给定一个整数n，生成所有由1...n为节点所组成的二叉搜索树。
           
思路        
首先要了解二叉搜索树的特点：           
1. 若任意节点的左子树不空，则左子树上所有节点的值均小于它的根节点的值；
2. 若任意节点的右子树不空，则右子树上所有节点的值均大于它的根节点的值；
3. 任意节点的左、右子树也分别为二叉查找树；
4. 没有键值相等的节点。
              
代码示例          
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<TreeNode> generateTrees(int n) {
        if(n<1){
            return new LinkedList<TreeNode>();
        }
        return generateSubtrees(1,n);
    }
    
    private List<TreeNode> generateSubtrees(int s,int e){
        List<TreeNode> res=new LinkedList<TreeNode>();
        if(s>e){
            res.add(null);
            return res;
        }
        for (int i = s; i <= e; ++i) {
        List<TreeNode> leftSubtrees = generateSubtrees(s, i - 1);
        List<TreeNode> rightSubtrees = generateSubtrees(i + 1, e);
        for (TreeNode left : leftSubtrees) {
            for (TreeNode right : rightSubtrees) {
                TreeNode root = new TreeNode(i);
                root.left = left;
                root.right = right;
                res.add(root);
            }
        }
    }
    return res;
    }
}
```
               
## 搜索