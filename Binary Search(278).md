### 278. [First Bad Version](https://leetcode.com/problems/first-bad-version/tabs/description)
>You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

>Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

>You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.
----
### Java
```
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int left = 1;
        int right = n;
        while(left<right){
            int mid = left+(right-left)/2;
            if(isBadVersion(mid))
                right = mid;
            else
                left = mid+1;
        }
        return left;
    }
}
/*
 Solution 1: Brute Force: Time limite exceed
   public int firstBadVersion(int n) {
        int i = 1;
        for(i = 1; i <= n; i++){
            if(isBadVersion(i)) 
                break;
        }
       return i; 
    }
    Time complexity : O(n)O(n)
Solution 2: Binary Search
   Note:If you are setting mid = (left + right)/2 , you have to be very careful. Unless you are using a language 
   that does not overflow such as Python, left + rightleft+right could overflow. One way to fix this is to use 
   left + (right - left)/2 instead.
   Time complexity : O(logn). The search space is halved each time, so the time complexity is O(logn).

*/
```
