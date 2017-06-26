### 326. [Power of Three](https://leetcode.com/problems/power-of-three/#/description) 
> Given an integer, write a function to determine if it is a power of three.  

>Follow up:  
>Could you do it without using any loop / recursion?  
----
### Java
```
public class Solution {
    public boolean isPowerOfThree(int n) {
    while(n != 0 && n != 1 && n % 3 == 0){   //while(n && n%3==0)
        n = n/3;
    } 
    return n==1;
    }
}
//power of three: 3的次方数
//think about zero and negative number
//reference: http://www.cnblogs.com/grandyang/p/5138212.html
//all solution: https://discuss.leetcode.com/topic/33536/a-summary-of-all-solutions-new-method-included-at-15-30pm-jan-8th
/*
public boolean isPowerOfThree(int n) {
    // 1162261467 is 3^19,  3^20 is bigger than int  
    return ( n>0 &&  1162261467%n==0);
}

public boolean isPowerOfThree(int n) {
    return n>0 && (n==1 || (n%3==0 && isPowerOfThree(n/3)));
}
*/
```
