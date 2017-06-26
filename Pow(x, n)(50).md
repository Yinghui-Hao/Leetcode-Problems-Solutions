### 50. [Pow(x, n)](https://leetcode.com/problems/powx-n/#/description)
>Implement pow(x, n). 
----
### Java
```
//with divide and conquer
public class Solution {
    public double myPow(double x, int n) {
        double res=1;
        while(n!=0)
        {
            if(n%2==0)
            {
                
                x=x*x;
                n/=2;
            }
            else
            {
                if(n>0)
                {
                    res*=x;
                    n--;
                }
                else
                {
                    res/=x;
                    n++;
                }
            }
        }
        return res;
    }
}
```
### C++
```
class Solution {
public:
    double myPow(double x, int n) {
        
        if (n == 0) return 1;
        if (n < 0) return 1/x * myPow(1/x, -(n+1));
        //if (n == 1) return x;
        //if (n == 2) return x*x;
        if (n % 2 == 0) return myPow(myPow(x, n/2), 2);
        else 
            return x * myPow(myPow(x, n/2), 2);//x*myPow(x*x, n/2);
    }
};
```
