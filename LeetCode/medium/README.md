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
/------------------------------------------------------------------------------------------------------------------------------/
1477. Find Two Non-overlapping Sub-arrays Each With Target Sum

You are given an array of integers arr and an integer target.
You have to find two non-overlapping sub-arrays of arr each with a sum equal target. There can be multiple answers so you have to find an answer where the sum of the lengths of the two sub-arrays is minimum.
Return the minimum sum of the lengths of the two required sub-arrays, or return -1 if you cannot find such two sub-arrays.

Constraints:
1 <= arr.length <= 105
1 <= arr[i] <= 1000
1 <= target <= 108

```cpp
class Solution {
public:
    int minSumOfLengths(vector<int>& A, int k) {
        int n = A.size();
        int res = n + 1, sum = 0, i = 0;

        vector<int> dp(n + 1, n);

        for (int j = 0; j < n; j++) {
            sum += A[j];

            while (sum > k)
                sum -= A[i++];

            dp[j + 1] = dp[j];

            if (sum == k) {
                res = min(res, j - i + 1 + dp[i]);
                dp[j + 1] = min(dp[j], j - i + 1);
            }
        }

        return res == n + 1 ? -1 : res;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/