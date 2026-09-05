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
/-------------------------------------------------------------------------------------------------------------------------/
/*1672. Richest Customer Wealth
You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the i​​​​​​​​​​​th​​​​ customer has in the j​​​​​​​​​​​th​​​​ bank. Return the wealth that the richest customer has.

A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.

Constraints:
m == accounts.length
n == accounts[i].length
1 <= m, n <= 50
1 <= accounts[i][j] <= 100*/

```cpp
class Solution{
public:
    int MaximunWealth(vector<vector<int>> & accounts){
        int maxwealth = 0;
        for(const auto & customer: accounts){
            int currentsum = 0;
            for(int val: customer){
                currentsum += val;
            }
            maxwealth = max(maxwealth,currentsum);
        }
        return maxwealth;
    }    
};
```

/----------------------------------------------------------------------------------------------------------------------------/
/*412. Fizz Buzz
Given an integer n, return a string array answer (1-indexed) where:

answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
answer[i] == "Fizz" if i is divisible by 3.
answer[i] == "Buzz" if i is divisible by 5.
answer[i] == i (as a string) if none of the above conditions are true.

Constraints:
1 <= n <= 104*/

```cpp
class Solution{
    public:
    vector<string> fizzBuzz(int n){
        vector<string> answer;
        // Pre allocate memory to prevent runtime resizing overhead
        answer.reserve(n);
        for(int i = 1; i<= n;i++){
            string current = "";

            if(i % 3 == 0) current += "Fizz";
            if(i % 5 == 0) current += "Buzz";

            if(current.empty()){
                current = to_string(i);
            }
            answer.push_back(current);
        }
        return answer;
    }
}
```

/---------------------------------------------------------------------------------------------------------------------------/
1342. Number of Steps to Reduce a Number to Zero

Given an integer num, return the number of steps to reduce it to zero.
In one step, if the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.

Constraints:
0 <= num <= 106

```cpp
class Solution{
    public:
    int numberOfSteps(int num){
        int currentstep = 0;
        while(num > 0){
            if(num % 2 == 0){
                num /= 2;
            }else{
                num -= 1;
            }
            currentstep ++;
        }return currentstep;
    }
};
```

/---------------------------------------------------------------------------------------------------------------------------/
1929. Concatenation of Array

Given an integer array nums of length n, you want to create an array ans of length 2n where ans[i] == nums[i] and ans[i + n] == nums[i] for 0 <= i < n (0-indexed).
Specifically, ans is the concatenation of two nums arrays.
Return the array ans.

Constraints:
n == nums.length
1 <= n <= 1000
1 <= nums[i] <= 1000

```cpp
class Solution{
    public:
    vector<int> getConcatenation(vector<int> &num){
        int n = nums.size();
        vector<int> ans(2*n);

        for(int i=0; i< n; i++){
            ans[i] = num[i];
            ans[i+n] = num[i];
        }return ans;
    }
};
```

/---------------------------------------------------------------------------------------------------------------------------/
1470. Shuffle the Array

Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].
Return the array in the form [x1,y1,x2,y2,...,xn,yn].

Constraints:
1 <= n <= 500
nums.length == 2n
1 <= nums[i] <= 10^3

```cpp
class Solutions{
    public:
    vector<int> shuffle(vector<int> &nums, int n){
        vector<int> ans(2 * n);

        for(int i = 0; i < n; i++){
            ans[2 * i] = nums[i];
            ans[2 * i + 1] = nums[i + n];
        }
        return ans;
    }
}

```
/---------------------------------------------------------------------------------------------------------------------------/
485. Max Consecutive Ones

Given a binary array nums, return the maximum number of consecutive 1's in the array.
 
Constraints:
1 <= nums.length <= 105
nums[i] is either 0 or 1.

```cpp
class Solution{
    public:
    int findMaxConsecutiveOnes(vector<int> &nums){
        int max_streak = 0;
        int count_streak = 0;

        for(int val:nums){
            count_streak = (val == 1) ? count_streak + 1: 0;
            max_streak = max(max_streak, count_streak);
        }
        return max_streak;
    }
}
```