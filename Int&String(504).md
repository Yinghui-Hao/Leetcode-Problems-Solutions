### 504. [Base 7](https://leetcode.com/problems/base-7/#/description)
>Given an integer, return its base 7 string representation.   
-----
### Java
```
public class Solution {
    public String convertToBase7(int num) {
        String res= "";// can also write String res=new String(""); cannot write String res=null, null is consider as string
        //if num is negative number
        int flag = 0;
        if(num<0){
            num = -num;
            flag = 1;
        }
        while(num >= 7){
            res = res + String.valueOf(num%7);
            num = num/7;
        }
        res = res + num;
        //reverse the string
        return flag==0?new StringBuilder(res).reverse().toString():"-"+new StringBuilder(res).reverse().toString();
    }
}
//简单题，求一个数的七进制 [−107,107]
//Java 中String的两种初始化方法：http://blog.csdn.net/cainiao123hack/article/details/7801179
/*
//with recursion
public String convertTo7(int num) {
    if (num < 0)
        return '-' + convertTo7(-num);
    if (num < 7)
        return num + "";
    return convertTo7(num / 7) + num % 7;
}

//with Java standard library
public String convertTo7(int num) {
    return Integer.toString(num, 7);
}

*/
```
