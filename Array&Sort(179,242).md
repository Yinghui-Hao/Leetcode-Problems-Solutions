### 179. [Largest Number](https://leetcode.com/problems/largest-number/#/solutions)
>Given a list of non negative integers, arrange them such that they form the largest number.  

>For example, given [3, 30, 34, 5, 9], the largest formed number is 9534330.  

>Note: The result may be very large, so you need to return a string instead of an integer.  
----
### Java
```
public class Solution {
     public String largestNumber(int[] num) {
		if(num == null || num.length == 0)
		    return "";
		
		// Convert int array to String array, so we can sort later on
		String[] s_num = new String[num.length];
		for(int i = 0; i < num.length; i++)
		    s_num[i] = String.valueOf(num[i]);
			
		// Comparator to decide which string should come first in concatenation
		Comparator<String> comp = new Comparator<String>(){
		    @Override
		    public int compare(String str1, String str2){
		        String s1 = str1 + str2;
			String s2 = str2 + str1;
			return s2.compareTo(s1); // reverse order here, so we can do append() later
		    }
	        };
		
		Arrays.sort(s_num, comp);
                // An extreme edge case by lc, say you have only a bunch of 0 in your int array
                if(s_num[0].charAt(0) == '0')
                    return "0";
            
		StringBuilder sb = new StringBuilder();
		for(String s: s_num)
	            sb.append(s);
		
		return sb.toString();
		
	}
}
//String的compareTo用法: http://wobfei.iteye.com/blog/743123
//java中Collection.sort排序详解： http://blog.csdn.net/tjcyjd/article/details/6804690
```

### 242.[Valid Anagram](https://leetcode.com/problems/valid-anagram/#/description)
>Given two strings s and t, write a function to determine if t is an anagram of s.  

>For example,  
>s = "anagram", t = "nagaram", return true.  
>s = "rat", t = "car", return false.  

>Note:  
>You may assume the string contains only lowercase alphabets.  
----
### Java
```
public class Solution {
    public boolean isAnagram(String s, String t) {
        if (s == t || s.equals(t)) {
           return true;
        }
        char[] sa = s.toCharArray();
        Arrays.sort(sa);
        String sr = String.valueOf(sa);//or String sr = new String(sa);
        char[] ta = t.toCharArray();
        Arrays.sort(ta);
        String tr = String.valueOf(ta);
        return sr.equals(tr);
    }
}
//change char array to string:  http://blog.csdn.net/guo0820/article/details/51194588
//java array: http://developer.51cto.com/art/200906/128274.htm
/*can be solve in three method: sort, hash, prime
2.Hash Array

public boolean isAnagram(String s, String t) {
    int[] hash = new int[26];
    for (int i = 0; i < s.length(); i++) {
        hash[s.charAt(i) - 'a']++;
    }
    for (int i = 0; i < t.length(); i++) {
        hash[t.charAt(i) - 'a']--;
    }
    for (int i = 0; i < hash.length; i++) {
        if (hash[i] != 0) {
            return false;
        }
    }
    return true;
}
//hash[s.charAt(i) - 'a']++: https://zhidao.baidu.com/question/179839401552881564.html
//https://zhidao.baidu.com/question/561514698.html

3.Prime

private static final int[] PRIMES = new int[]{3, 5, 7, 11 ,13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71,
        73, 79, 83, 89, 97, 101, 107};
public boolean isAnagram(String s, String t) {
    return hash(s) == hash(t);
}

private long hash(String s) {
    long hash = 1;
    for (int i = 0; i < s.length(); i++) {
        hash *= PRIMES[s.charAt(i) - 'a'];
    }
    return hash;
}
//Prime Promblem: 素数，又称质数，除1和它本身不再有其他因数

*/
```
