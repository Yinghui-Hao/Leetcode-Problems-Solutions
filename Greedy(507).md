### 507. [Perfect Number](https://leetcode.com/problems/perfect-number/#/description)
>We define the Perfect Number is a positive integer that is equal to the sum of all its positive divisors except itself.   
>Now, given an integer n, write a function that returns true when it is a perfect number and false when it is not.   

>Example:   
>Input: 28  
>Output: True  
>Explanation: 28 = 1 + 2 + 4 + 7 + 14  
----
### Java
```
public class Solution {
    public boolean checkPerfectNumber(int num) {
    if(num<=1) return false;
    int sum = 0;
    for(int i = 1;i<=num/i;i++){
        if(num%i==0){
            sum+=i;
            if(i!=sum/i){
                sum+=num/i;
            }
        }
    }
    return sum==num;
    /**public boolean checkPerfectNumber(int num) {
        int result = 1;
        if(num >= Math.pow(2,8) || num <= 0 || num == 1){
            return false;
        }
        for(int i = 2 ; i < num ; i ++ ){
            if(num % i == 0){
                result+= i;
            }
        }
        if(result == num){
            return true;
        }else{
            return false;
        }**/
        
    }
}
/**public boolean checkPerfectNumber(int num) {
    if(num<=1) return false;
    int sum = 0;
    for(int i = 1;i<=num/i;i++){
        if(num%i==0){
            sum+=i;
            if(i!=sum/i){
                sum+=num/i;
            }
        }
    }
    return sum==num;
}**/
```
