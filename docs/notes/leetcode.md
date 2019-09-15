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
## 分治
## 搜索