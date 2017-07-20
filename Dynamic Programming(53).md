### 53. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/#/description)
> Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

>For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
>the contiguous subarray [4,-1,2,1] has the largest sum = 6.
----
### Java
```
public class Solution {
    // public int maxSubArray(int[] nums) {
    //     int max = nums[0];
    //     int sum = 0;
    //     int j = 0;
    //     for(int i = 0; i < nums.length; i++){
    //         sum = sum + nums[i];
    //         if(sum >= max) max = sum;
    //         else{
    //             if(sum<nums[i])
    //             sum = nums[i];
    //         } 
    //     }
    //     return max;
    // }
    public int maxSubArray(int[] nums) {
    int currMax=nums[0],max=nums[0];
    for(int i=1;i<nums.length;i++){
        currMax=Math.max(currMax+nums[i],nums[i]);
        max=Math.max(max,currMax);
    }
    return max;
}
}
```
//[using DP Algorithm](https://discuss.leetcode.com/topic/6413/dp-solution-some-thoughts)
