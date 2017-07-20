### 53. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/#/description)
> Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

>For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
>the contiguous subarray [4,-1,2,1] has the largest sum = 6.
----
### Java
```
public class Solution {
     public int maxSubArray(int[] nums) {
        int max = nums[0];
        int sum = 0;
        int j = 0;
        for(int i = 0; i < nums.length; i++){
            sum = sum + nums[i];
            if(sum >= max) max = sum;
           // else{
                if(sum<0)
                sum = 0;
           // } 
        }
        return max;
    } 
}
/*
Solution 1:
 public int maxSubArray(int[] nums) {
    int currMax=nums[0],max=nums[0];
    for(int i=1;i<nums.length;i++){
        currMax=Math.max(currMax+nums[i],nums[i]);
        max=Math.max(max,currMax);
    }
    return max;
}

Solution 2: maxSubArray(A, i) = maxSubArray(A, i - 1) > 0 ? maxSubArray(A, i - 1) : 0 + A[i]; 
public int maxSubArray(int[] A) {
        int n = A.length;
        int[] dp = new int[n];//dp[i] means the maximum subarray ending with A[i];
        dp[0] = A[0];
        int max = dp[0];
        
        for(int i = 1; i < n; i++){
            dp[i] = A[i] + (dp[i - 1] > 0 ? dp[i - 1] : 0);
            max = Math.max(max, dp[i]);
        }
        
        return max;
}
*/
```
//[using DP Algorithm](https://discuss.leetcode.com/topic/6413/dp-solution-some-thoughts)
