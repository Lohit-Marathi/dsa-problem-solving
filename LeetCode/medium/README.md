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
15. 3Sum

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.
Notice that the solution set must not contain duplicate triplets.

Example 1:
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.



Constraints:
3 <= nums.length <= 3000
-105 <= nums[i] <= 105

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        vector<vector<int>> triplets;
        int n = nums.size();
        sort(nums.begin(),nums.end());

        for(int i = 0; i < n-2; i++){
            if(nums[i] > 0) break;

            if(i > 0 && nums[i] == nums[i-1]) continue;

            int left = i+1;
            int right = n -1;
            while(left<right){
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0){
                    triplets.push_back({nums[i],nums[left],nums[right]});
                

                    while(left < right && nums[left] == nums[left + 1]) left ++;
                    while(left<right && nums[right] == nums[right - 1]) right --;

                    left ++;
                    right --;
                }
                else if (sum < 0){
                left ++;
                }
                else{
                right --;
                }
            }
            
        }return triplets;
    }
};

```