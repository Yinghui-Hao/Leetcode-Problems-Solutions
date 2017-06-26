### 7. [Reverse Integer](https://leetcode.com/problems/reverse-integer/#/description)
>Reverse digits of an integer.  

>Example1: x = 123, return 321  
>Example2: x = -123, return -321   
----
### Java
```
public class Solution {
    public int reverse(int x) {
        int res = 0;  
        while(x != 0)  
        {   
            int tail =x%10;
            int newres = res * 10 + tail;
            //the reverse number can be overflow, so we avoid this below
            if ((newres - tail) / 10 != res)
             { return 0; }
             res=newres;
            x /= 10;  
        }  
        return res;  
    }
}
/*
int reverse(int x)  
    {  
        int res = 0;  
        while(x > 0)  
        {  
            res = res * 10 + x %10;  
            x /= 10;  
        }  
        return res;  
    }  
    
public class Solution {
    public int reverse(int x) {
       // String s = Integer.toBinaryString(x);
        String num = String.valueOf(x);
        //if(x < Integer.MIN_VALUE || x > Integer.MAX_VALUE){
        //    return 0;
       // }
        if(x >= 0){
            String sb = new StringBuffer(num).reverse().toString();
            return Integer.parseInt(sb);
        }
        else{
            String num2 = num.substring(1);
            String sb = new StringBuffer(num2).reverse().toString();
            return 0-Integer.parseInt(sb);
        }
        
    }
}*/

//Java 如何将String转化为Int https://zhidao.baidu.com/question/38519769.html
/**public int rever(int x){
		long r = 0;
		while(x != 0){
			r = r*10 + x%10;
			x /= 10;
		}
		if(r >= Integer.MIN_VALUE && r <= Integer.MAX_VALUE)
			return (int)r;
		else
			return 0;
	}**/
```
### 9. [Palindrome Number](https://leetcode.com/problems/palindrome-number/#/description)
>Determine whether an integer is a palindrome. Do this without extra space.  
----
### Java
```
public class Solution {
    public boolean isPalindrome(int x) {
        int num =x;
        int res = 0;
        int newres = 0;
        int tail = 0;
        if(x<0) return false;
        //if(x>=0&&x<=9) return true;
        while(x != 0)  
        {   
            tail =x%10;
            newres = res * 10 + tail;
            //the reverse number can be overflow, so we avoid this below
            if ((newres - tail) / 10 != res)
             { return false; }
             res=newres;
            x /= 10;  
        }  
        return res==num;
    }
}
```
