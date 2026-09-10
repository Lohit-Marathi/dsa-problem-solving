50. Pow(x, n)
Implement pow(x, n), which calculates x raised to the power n (i.e., xn).

Constraints:
-100.0 < x < 100.0
-231 <= n <= 231-1
n is an integer.
Either x is not zero or n > 0.
-104 <= xn <= 104

```cpp
class Solution{
    public:
    double myPow(double x,int n){
        long long N = n;

        if(N < 0){
            x = 1.0 / x;
            N = -N;
        }
        double ans = 1.0;

        while(N > 0){
            if(N % 2 != 0){
                ans  *= x;
            }
            x *= x;
            N /= 2;
        }
        return ans;
    }
}
```