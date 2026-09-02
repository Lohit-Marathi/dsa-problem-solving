/*2235. Add Two Integers
Given two integers num1 and num2, return the sum of the two integers.
 
Constraints:  -100 <= num1, num2 <= 100*/

```cpp
class Solutions{
    public:
    int sum(int num1, int num2){
        return num1 + num2;
    }
};
```
/------------------------------------------------------------------------------------------------------------------------------/
/*1480. Running Sum of 1d Array
Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).Return the running sum of nums.

 Constraints:
 1 <= nums.length <= 1000
-10^6 <= nums[i] <= 10^6*/

```cpp
class Solution{
    public:
    vector<int> runningSum(vector<int> &nums){
        for(int i = 1;i < nums.size(); i++){
            nums[i] = nums[i] + nums[i-1];
        }
        return nums;
    }
};
```