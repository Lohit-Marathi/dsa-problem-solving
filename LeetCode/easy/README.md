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