### 35. [Search Insert Position](https://leetcode.com/problems/search-insert-position/#/description) 
>Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

>You may assume no duplicates in the array.  

>Here are few examples.  
>[1,3,5,6], 5 → 2  
>[1,3,5,6], 2 → 1  
>[1,3,5,6], 7 → 4  
>[1,3,5,6], 0 → 0   
----
### Java
```
public class Solution {
    public int searchInsert(int[] nums, int target) {
       if(nums.length == 0) return 0;
       int i = 0;
       for(i = 0; i < nums.length; i++){
          if(nums[i] >= target) break; 
       } 
       return i;
    }
}

/*
 public int searchInsert(int[] A, int target) {
        int low = 0, high = A.length-1;
        while(low<=high){
            int mid = (low+high)/2;
            if(A[mid] == target) return mid;
            else if(A[mid] > target) high = mid-1;
            else low = mid+1;
        }
        return low;
    }
    
public class Solution {
public int searchInsert(int[] nums, int target) {
    int low = 0, high = nums.length;
    while(low < high) {
        int mid = low + (high - low) / 2;
        if(nums[mid] < target)
            low = mid + 1;
        else
            high = mid;
    }
    return low;
}
*/
```
### 88.[ Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/#/description)
>Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

>Note:
>You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number >of elements initialized in nums1 and nums2 are m and n respectively.  
----
### Java
```
public class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m-1;
        int j = n-1;
        int k = m+n-1;
        while(i >= 0 && j >= 0){
            if(nums1[i]>nums2[j])
                nums1[k--] = nums1[i--];
            else{
                nums1[k--] = nums2[j--];
            }
        }
        while(j>=0){
            nums1[k--] = nums2[j--];
        }   
    }
}

//two sorted array
//num1数组的空间足够，那么就考虑从后往前赋值以避免数值覆盖
```
