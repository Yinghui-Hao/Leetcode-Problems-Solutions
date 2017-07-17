### 168. [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/#/description)
>Given a positive integer, return its corresponding column title as appear in an Excel sheet. 
```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
```
----
### Java
```
public class Solution {
    public String convertToTitle(int n) {
        StringBuilder result = new StringBuilder();

        while(n>0){
            n--;
            result.insert(0, (char)('A' + n % 26));
            n /= 26;
        }

        return result.toString();
    }
}
/*
StringBuilder/StringBuffer的insert, append复杂度分析: http://blog.csdn.net/xiaoxixixiyang/article/details/40377187

string convertToTitle(int n) {
        string ans;
        while (n) {
            ans = char ((n - 1) % 26 + 'A') + ans;
            n = (n - 1) / 26;
        }
        return ans;
    }

*/
```
### 28. [Implement strStr()](https://leetcode.com/problems/implement-strstr/#/description)
>Implement strStr().  

>Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.  
----
### Java
```
public class Solution {
    public int strStr(String haystack, String needle) {
        int hlen = haystack.length();
        int nlen = needle.length();
        if(hlen < nlen) return -1;
        else if(nlen == 0) return 0;
        int threshold = hlen - nlen;
        for(int i = 0; i <= threshold; i++){
            if(haystack.substring(i, i + nlen).equals(needle)){
                return i;
            }
        }
        return -1;
    }
}

/*
public int strStr(String haystack, String needle) {
  for (int i = 0; ; i++) {
    for (int j = 0; ; j++) {
      if (j == needle.length()) return i;
      if (i + j == haystack.length()) return -1;
      if (needle.charAt(j) != haystack.charAt(i + j)) break;
    }
  }
}
1.实现strstr(). 返回needle(关键字)在haystack(字符串)中第一次出现的位置，如果needle不在haystack中，则返回-1。
2.substring(参数)是java中截取字符串的一个方法
有两种传参方式
一种是public String substring(int beginIndex)
返回一个新的字符串，它是此字符串的一个子字符串。该子字符串从指定索引处的字符开始，直到此字符串末尾。
另一种是public String substring(int beginIndex, int endIndex)
返回一个新字符串，它是此字符串的一个子字符串。该子字符串从指定的 beginIndex 处开始，直到索引 endIndex - 1 处的字符。
因此，该子字符串的长度为 endIndex-beginIndex。 
3. java中length,length(),size()区别: http://www.cnblogs.com/hnrainll/archive/2012/10/29/2744492.html
    (1) java中的length属性是针对数组说的,比如说你声明了一个数组,想知道这个数组的长度则用到了length这个属性.
    (2) java中的length()方法是针对字符串String说的,如果想看这个字符串的长度则用到length()这个方法.
    (3) java中的size()方法是针对泛型集合说的,如果想看这个泛型有多少个元素,就调用此方法来查看
*/
```
