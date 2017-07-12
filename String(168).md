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
