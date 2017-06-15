### 605. [Can Place Flowers](https://leetcode.com/problems/can-place-flowers/#/description)
>Suppose you have a long flowerbed in which some of the plots are planted and some are not. However, flowers cannot be planted in adjacent plots - they would compete for water and both would die.  

>Given a flowerbed (represented as an array containing 0 and 1, where 0 means empty and 1 means not empty), and a number n, return if n new flowers can be planted in it without violating the no-adjacent-flowers rule.  
----
### Java
```
public class Solution {
    public boolean canPlaceFlowers(int[] bed, int n) {
        int length=bed.length;
        if(length==1&&bed[0]==0){
            n--;
        }
        else if(length==1&&bed[0]==1){
            return n==0;
        }
        if(length>=2){
        if(bed[0]==0&&bed[1]==0){
            bed[0]=1;
            n--;
        }
        if(bed[length-1]==0&&bed[length-2]==0){
            bed[length-1]=1;
            n--;
        }
        }
        if(length>=3){
        for (int i = 1; i < bed.length; i++) {
            if (bed[i] == 0 && bed[i-1] == 0 &&  bed[i+1] == 0) {
                bed[i] = 1;
                n--;
            }
        }
        }
        return n <= 0;        
    }
}
/**public class Solution {
    public boolean canPlaceFlowers(int[] bed, int n) {
        for (int i = 0; i < bed.length; i++) {
            if (bed[i] == 0 && (i == 0 || bed[i - 1] == 0) && (i == bed.length - 1 || bed[i + 1] == 0)) {
                bed[i] = 1;
                n--;
            }
        }
        return n <= 0;        
    }
}**/ 
/*public class Solution {
    public boolean canPlaceFlowers(int[] bed, int n) {
        int length=bed.length;
        if(bed[0]==0&&bed[1]==0){
            bed[0]=1;
            n--;
        }
        if(bed[length-1]==0&&bed[length-2]==0){
            bed[length-1]=1;
            n--;
        }
        for (int i = 1; i < bed.length; i++) {
            if (bed[i] == 0 && bed[i - 1] == 0 &&  bed[i + 1] == 0)) {
                bed[i] = 1;
                n--;
            }
        }
        return n <= 0;        
    }
}*/
```
