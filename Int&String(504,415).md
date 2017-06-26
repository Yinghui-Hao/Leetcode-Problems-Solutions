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
### 415. [Add Strings](https://leetcode.com/problems/add-strings/#/description)
>Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2.  

>Note:  
>>    1. The length of both num1 and num2 is < 5100.  
>>    2. Both num1 and num2 contains only digits 0-9.  
>>    3. Both num1 and num2 does not contain any leading zero.  
>>    4. You must not use any built-in BigInteger library or convert the inputs to integer directly.  
----
### Java
```
public class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder sb = new StringBuilder();
        int carry = 0;
        for(int i = num1.length() - 1, j = num2.length() - 1; i >= 0 || j >= 0 || carry == 1; i--, j--){
            //when x y have different bits of integer
            int x = i < 0 ? 0 : num1.charAt(i) - '0';
            int y = j < 0 ? 0 : num2.charAt(j) - '0';
            sb.append((x + y + carry) % 10);
            carry = (x + y + carry) / 10;
        }
        return sb.reverse().toString();
        
    }
}
//string转成int的几种方法: http://www.cnblogs.com/bemawen/archive/2012/12/10/2812076.html
//s.charAt(i)-'0' 是去取字符的uincode值， digit整型对应的也是个字符。 https://zhidao.baidu.com/question/179839401552881564.html
```


