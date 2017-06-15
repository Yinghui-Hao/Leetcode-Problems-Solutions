## 461. [Hamming Distance](https://leetcode.com/problems/hamming-distance/#/description)
>The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

>Given two integers x and y, calculate the Hamming distance.
>Note: 0 ≤ x, y < 231. 
----
## Java
```
public class Solution {
    public int hammingDistance(int x, int y) {
        long a = x;
        long b = y;
        long c = a^b;
        int z = Long.bitCount(c);
        return z;
    }
}
//int——> long: https://zhidao.baidu.com/question/937477520637551372.html
//a^b：
https://zhidao.baidu.com/question/546464855.html?device=mobile&ssid=7c74d3eab9fdccecc7e7485948b92b&from=0&uid=0&pu=usm@0,sz@1320_2001,ta@iphone_1_10.1_3_602&bd_page_type=1&baiduid=9449ECAF2EF34B376D0A1594D4983577&tj=www_zhidao_normal_1_0_10_title
```
