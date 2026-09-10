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

/---------------------------------------------------------------------------------------------------------------------------/
645. Set Mismatch

You have a set of integers s, which originally contains all the numbers from 1 to n. Unfortunately, due to some error, one of the numbers in s got duplicated to another number in the set, which results in repetition of one number and loss of another number.

You are given an integer array nums representing the data status of this set after the error.
Find the number that occurs twice and the number that is missing and return them in the form of an array.

Constraints:
2 <= nums.length <= 104
1 <= nums[i] <= 104

```cpp
class Solution {
public:
    std::vector<int> findErrorNums(const std::vector<int>& nums) {
        long long n = nums.size();
    
        long long ideal_sum = n * (n + 1) / 2;
        long long ideal_sq_sum = n * (n + 1) * (2 * n + 1) / 6;
        
        long long actual_sum = 0;
        long long actual_sq_sum = 0;
        for (int num : nums) {
            actual_sum += num;
            actual_sq_sum += (long long)num * num;
        }
    
        long long diff_linear = actual_sum - ideal_sum;       
        long long diff_squared = actual_sq_sum - ideal_sq_sum; 
        
        long long sum_linear = diff_squared / diff_linear;     
        
        int duplicate = (diff_linear + sum_linear) / 2;
        int missing = sum_linear - duplicate;
        
        return {duplicate, missing};
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
1365. How Many Numbers Are Smaller Than the Current Number

Given the array nums, for each nums[i] find out how many numbers in the array are smaller than it. That is, for each nums[i] you have to count the number of valid j's such that j != i and nums[j] < nums[i].
Return the answer in an array.

Constraints:
2 <= nums.length <= 500
0 <= nums[i] <= 100

```cpp
class Solution {
    public:
    vector<int> smallerNumberThanCurrent(vector<int> &nums){
        unordered_map<int,int> = my_map;
        int n = size(nums);
        vector<int> sorted(nums);
        sort(sorted.begin(),sorted.end());

        for(int i = 0; i < n; i++){
            if(my_map.find(sorted[i]) == my_map.end()){
                my_map.sorted[i] = i;
            }
        }
        for(i = 0; i< n; i++){
            sorted[i] = my_map[nums[i]];
        }
        return sorted;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
1. Two Sum

You are given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

Constraints:
2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        int n = size(nums);
        unordered_map<int,int> hash;

        for(int i = 0; i < n; i++){
            hash[nums[i]] = i;
        }
        for(int i = 0; i < n; i++){
            int complement = target - nums[i];
            if(hash.find(complement) != hash.end() && hash[complement] != i){
                return { i, hash[complement]};
            }
        }
        return {};
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
169. Majority Element

Given an array nums of size n, return the majority element.
The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.
 
Constraints:
n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109
The input is generated such that a majority element will exist in the array.
Follow-up: Could you solve the problem in linear time and in O(1) space?

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[nums.size()/2]; 
    }
};
```

/---------------------------------------------------------------------------------------------------------------------------/
125. Valid Palindrome

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.
Given a string s, return true if it is a palindrome, or false otherwise.

Constraints:
1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.

```cpp
auto init = []() {
    std::ios_base::sync_with_stdio(false);
    std::cin.tie(nullptr);
    return 0;
}();
class Solution {
public:
    bool isPalindrome(string s) {
        int left = 0;
        int right = s.length() - 1;

        while(left<right){
            while(left<right && !isalnum(static_cast<unsigned char> (s[left]))){
                left ++;
            }
            while(left<right && !isalnum(static_cast<unsigned char> (s[right]))){
                right --;
            }

            if(tolower(static_cast<unsigned char> (s[left])) != tolower(static_cast<unsigned char> (s[right]))){
                return false;
            }
            left ++;
            right --;
        }return true;
    }    
};
```
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/
/---------------------------------------------------------------------------------------------------------------------------/

