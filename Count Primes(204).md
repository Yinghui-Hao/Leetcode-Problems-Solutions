### 204.[Count Primes](https://leetcode.com/problems/count-primes/tabs/description)
>Count the number of prime numbers less than a non-negative number, n.
----
### Java
```
public class Solution {
    public int countPrimes(int n) {
        
    }
}
/*
质数（prime number）又称素数，有无限个。一个大于1的自然数，除了1和它本身外，不能被其他自然数整除，换句话说就是该数除了
1和它本身以外不再有其他的因数；
否则称为合数。最小的质数是2。
自然数（natural number）0,1,2,3...

Solution: 埃拉托斯特尼筛法Sieve of Eratosthenes  http://www.cnblogs.com/grandyang/p/4462810.html
it starts from 2, the first prime, then mark the multip of 2 as true in notPrime, so the loop of i will skip them.
the next prime is 3, do the same thing. Then it is 4, which 2*2, so the not prime is true, and will skip to next.
            public int countPrimes(int n) {
                    boolean[] notPrime = new boolean[n];
                    int count = 0;
                    for (int i = 2; i < n; i++) {
                        if (notPrime[i] == false) {
                            count++;
                            for (int j = 2; i*j < n; j++) {
                                notPrime[i*j] = true;
                            }
                        }
                    }

                    return count;
                }
*/
```
