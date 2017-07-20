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
