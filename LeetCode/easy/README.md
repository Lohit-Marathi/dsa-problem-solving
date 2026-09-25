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
2965. Find Missing and Repeated Values

You are given a 0-indexed 2D integer matrix grid of size n * n with values in the range [1, n2]. Each integer appears exactly once except a which appears twice and b which is missing. The task is to find the repeating and missing numbers a and b.
Return a 0-indexed integer array ans of size 2 where ans[0] equals to a and ans[1] equals to b.

Constraints:
2 <= n == grid.length == grid[i].length <= 50
1 <= grid[i][j] <= n * n
For all x that 1 <= x <= n * n there is exactly one x that is not equal to any of the grid members.
For all x that 1 <= x <= n * n there is exactly one x that is equal to exactly two of the grid members.
For all x that 1 <= x <= n * n except two of them there is exactly one pair of i, j that 0 <= i, j <= n - 1 and grid[i][j] == x.

```cpp
class Solution {
public:
    vector<int> findMissingAndRepeatedValues(vector<vector<int>>& grid) {
        
        long long n = grid.size();
        long long k = n * n;

        long long expected_sum = k*(k+1)/2;
        long long expectedsquare_sum = k*(k+1) * (2*k + 1) / 6;

        long long actual_sum = 0;
        long long actualsquare_sum = 0;

        for(int i = 0; i < n; ++i){
            for(int j = 0; j < n; ++j){
                long long val = grid[i][j];
                actual_sum += val;
                actualsquare_sum += val * val;        
            }
        }

        long long diff1 = actual_sum - expected_sum;

        long long diff2 = actualsquare_sum - expectedsquare_sum;

        long long sum = diff2/diff1;

        int duplicate = (diff1 + sum)/2;
        int missing = sum - duplicate;

        return {duplicate,missing}; 
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
88. Merge Sorted Array

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.
The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

Constraints:
nums1.length == m + n
nums2.length == n
0 <= m, n <= 200
1 <= m + n <= 200
-109 <= nums1[i], nums2[j] <= 109

```cpp
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int i = m -1;
        int j = n - 1;
        int k = m + n -1;

        while(i>=0 && j>=0){
            if(nums1[i]>nums2[j]){
                nums1[k] = nums1[i];
                --i;
            }else{
                nums1[k] = nums2[j];
                --j;
            }
            --k;
        }
        while(j>=0){
            nums1[k] = nums2[j];
            --j;
            --k;
        }
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
136. Single Number

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.
You must implement a solution with a linear runtime complexity and use only constant extra space.

Constraints:
1 <= nums.length <= 3 * 104
-3 * 104 <= nums[i] <= 3 * 104
Each element in the array appears twice except for one element which appears only once.

```cpp
class Solution{
    public:
    int singleNumber(vector<int> &nums){
        int ans = 0;
        for(int num:nums){
            ans ^= num;
        }
        return ans;
    }
}
```
/---------------------------------------------------------------------------------------------------------------------------/

28. Find the Index of the First Occurrence in a String

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

Constraints:
1 <= haystack.length, needle.length <= 104
haystack and needle consist of only lowercase English characters.

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        for i in range(len(haystack) - len(needle) + 1):
            if haystack[i: i + len(needle)] == needle:
                return i
        return -1
```
/---------------------------------------------------------------------------------------------------------------------------/
35. Search Insert Position

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You must write an algorithm with O(log n) runtime complexity.

Constraints:
1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums contains distinct values sorted in ascending order.
-104 <= target <= 104

```python
class Solution:
    def searchIndex(self, nums:list[int], target: int)-> int:
        left, right = 0, len(nums) - 1

        while left <= right:
            mid = left + (right - left) // 2   // to stop the integer overflow 

            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return left
```
/---------------------------------------------------------------------------------------------------------------------------/
121. Best Time to Buy and Sell Stock

You are given an array prices where prices[i] is the price of a given stock on the ith day.
You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Constraints:
1 <= prices.length <= 105
0 <= prices[i] <= 104

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int min_price = INT_MAX;
        int max_profit = 0;
        for(int price:prices){
            if(price < min_price){
                min_price = price;
            }
            else if(price - min_price > max_profit){
                max_profit = price - min_price;
            }
        }
        return max_profit;
        
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/

14. Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".

Constraints:
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters if it is non-empty.

```cpp
//method 1
class Solution {
public:
    std::string longestCommonPrefix(std::vector<std::string>& strs) {
        // 1. Edge Case: If the array is empty, return ""
        if (strs.empty()) return "";
        
        // 2. Take the first string as our reference baseline
        std::string base = strs[0];
        
        // 3. Scan vertically, character by character
        for (int i = 0; i < base.length(); i++) {
            char c = base[i];
            
            // Check this character against all other strings
            for (int j = 1; j < strs.size(); j++) {
                // If the current index is out of bounds for the other string,
                // or if the characters don't match, we stop immediately.
                if (i >= strs[j].length() || strs[j][i] != c) {
                    return base.substr(0, i); // Return everything up to this point
                }
            }
        }
        
        return base;
    }
};

//method 2
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        //Handle empty input
        if(strs.empty()) return "";

        // sort the string alphabetically
        sort(strs.begin(),strs.end());
        
        //compare first and last strings
        string first = strs.front();
        string last = strs.back();
        string result = "";

        //Find the common characters between first and last string
        for(int i = 0; i< min(first.length(),last.length());i++){
            if(first[i] != last[i]){
                break;
            }
            result += first[i];
        }return result;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
242. Valid Anagram

Given two strings s and t, return true if t is an anagram of s, and false otherwise.

Constraints:
1 <= s.length, t.length <= 5 * 104
s and t consist of lowercase English letters.

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.length() != t.length()){
            return false;
        }
        int arr[26] = {0};
        for(char c : s){
            arr[c -'a']++;
        }
        for(char c : t){
            if(--arr[c-'a'] < 0){
                return false;
            }
        }
        return true;
    }
};

// class Solution {
// public:
//     bool isAnagram(const string& s, const string& t) {
//         // Force the compiler to decouple standard I/O synchronization
//         ios_base::sync_with_stdio(false);
//         cin.tie(NULL);

//         int len = s.length();
//         if (len != t.length()) return false;

//         // Use size_t or unsigned long long for faster CPU register matching
//         size_t counts[26] = {0};

//         // Pointer-arithmetic read (Faster than array indexing s[i])
//         const char* pS = s.data();
//         const char* pT = t.data();

//         // Loop Unrolling: Process 4 characters at a time to maximize instruction-level parallelism
//         int i = 0;
//         for (; i <= len - 4; i += 4) {
//             counts[pS[i] - 'a']++;     counts[pT[i] - 'a']--;
//             counts[pS[i+1] - 'a']++;   counts[pT[i+1] - 'a']--;
//             counts[pS[i+2] - 'a']++;   counts[pT[i+2] - 'a']--;
//             counts[pS[i+3] - 'a']++;   counts[pT[i+3] - 'a']--;
//         }

//         // Clean up remaining characters
//         for (; i < len; ++i) {
//             counts[pS[i] - 'a']++;
//             counts[pT[i] - 'a']--;
//         }

//         // Vectorized SIMD-friendly reduction
//         for (int j = 0; j < 26; ++j) {
//             if (counts[j] != 0) return false;
//         }

//         return true;
//     }
// };
```
/---------------------------------------------------------------------------------------------------------------------------/
9. Palindrome Number
Given an integer x, return true if x is a palindrome, and false otherwise.

Constraints:
-231 <= x <= 231 - 1

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) {
            return false;
        }

        long reverse = 0;
        int xcopy = x;

        while (x > 0) {
            if(reverse > INT_MAX/10){
                return false;
            }
            reverse = (reverse * 10) + (x % 10);
            x /= 10;
        }

        return reverse == xcopy;        
    }
};
// class Solution {
// public:
//     bool isPalindrome(int x) {
//         ios_base::sync_with_stdio(false);
//         cin.tie(NULL);

//         if(x < 0 || (x % 10 == 0 && x != 0)){
//             return false;
//         }
//         int revhalf = 0;   
//         while(x>revhalf){
//             if(revhalf > INT_MAX / 10){
//                 return false;
//             }
//             revhalf = (revhalf * 10) + (x % 10);
//             x /= 10;
//         }
//         return x == revhalf || x == revhalf / 10;
        
//     }
// };
```
/---------------------------------------------------------------------------------------------------------------------------/
13. Roman to Integer
Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:
I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.

Constraints:
1 <= s.length <= 15
s contains only the characters ('I', 'V', 'X', 'L', 'C', 'D', 'M').
It is guaranteed that s is a valid roman numeral in the range [1, 3999].

```cpp
class Solution {
public:
    int romanToInt(string s) {
        ios_base::sync_with_stdio(false);
        cin.tie(NULL);
        int ans = 0;
        unordered_map<char,int> c = {
            {'I',1},{'V',5},{'X',10},{'L',50},{'C',100},{'D',500},{'M',1000}
        }; 
        int n = s.length();
        for(int i=0; i<n ;i++){
            if(i < n-1 && c[s[i]] < c[s[i+1]]){
                ans -= c[s[i]];
            }else{
            ans += c[s[i]];
            }
        }return ans;
    }
};  
// class Solution {
// public:
//     int romanToInt(string s) {
//         int res = 0;
//         unordered_map<char, int> roman = {
//             {'I', 1},
//             {'V', 5},
//             {'X', 10}, 
//             {'L', 50},
//             {'C', 100},
//             {'D', 500},
//             {'M', 1000}
//         };

//         for (int i = 0; i < s.size() - 1; i++) {
//             if (roman[s[i]] < roman[s[i + 1]]) {
//                 res -= roman[s[i]];
//             } else {
//                 res += roman[s[i]];
//             }
//         }

//         return res + roman[s[s.size() - 1]];        
//     }
// };

```
/---------------------------------------------------------------------------------------------------------------------------/
20. Valid Parentheses

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
An input string is valid if:
Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.

Constraints:
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.

```cpp
class Solution {
public:
    bool isValid(string s) {
        // odd length strings can never be valid
        if(s.length() % 2 != 0) return false;

        stack<char> st;

        for(char val:s){
        //if it's opening bracket, push it's corresponding closing bracket
            if(val == '('){
                st.push(')');
            }else if(val == '{'){
                st.push('}');
            }else if(val== '['){
                st.push(']');
            }
            //if it's a closing bracket, ckeck if it matches the expected top element
            else{
                if(st.empty() || st.top() != val){
                    return false;
                }
                st.pop();  //matched successfully 
            }
        
        }
        // if the stack is empty, all the brackets were correctly matched
        return st.empty();
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
26. Remove Duplicates from Sorted Array
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.
Consider the number of unique elements in nums to be k​​​​​​​​​​​​​​. After removing duplicates, return the number of unique elements k.
The first k elements of nums should contain the unique numbers in sorted order. The remaining elements beyond index k - 1 can be ignored.

Custom Judge:
The judge will test your solution with the following code:

int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
If all assertions pass, then your solution will be accepted.
Example 2:
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).
 
Constraints:
1 <= nums.length <= 3 * 104
-100 <= nums[i] <= 100
nums is sorted in non-decreasing order.

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int i = 0; //index of last unique element

        for(int j = 0; j<nums.size(); j++){
            //found a new unique element
            if(nums[j] != nums[i]){
                nums[++i] = nums[j];
            }
        }
        return i + 1;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
21. Merge Two Sorted Lists

You are given the heads of two sorted linked lists list1 and list2.
Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.
Return the head of the merged linked list.

Example 1:
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
Example 2:

Constraints:
The number of nodes in both lists is in the range [0, 50].
-100 <= Node.val <= 100
Both list1 and list2 are sorted in non-decreasing order.

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode dummy(0);
        ListNode* tail = &dummy;

        while(list1 != nullptr && list2 != nullptr){
            if(list1->val <= list2 -> val){
                tail->next = list1;
                list1 = list1->next;
            }else{
                tail->next = list2;
                list2 = list2->next;
            }
            tail = tail->next;
        }
        if(list1 != nullptr){
            tail->next = list1;
        }else{
            tail->next = list2;
        }
        return dummy.next;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
27. Remove Element

Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.
Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:
Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.

Example 1:
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).

Constraints:
0 <= nums.length <= 100
0 <= nums[i] <= 50
0 <= val <= 100


```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int k = 0; // index of last unique number

        for(int j=0; j<nums.size();j++){
            // found a unique element
            if(nums[j] != val){
                nums[k] = nums[j];
                k++;
            }  
        }
        return k;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
58. Length of Last Word

Given a string s consisting of words and spaces, return the length of the last word in the string.
A word is a maximal substring consisting of non-space characters only.

Example 1:
Input: s = "Hello World"
Output: 5
Explanation: The last word is "World" with length 5.

Constraints:
1 <= s.length <= 104
s consists of only English letters and spaces ' '.
There will be at least one word in s.

```cpp
class Solution {
public:
    int lengthOfLastWord(string s) {
        int length = 0;
        int i = s.length() - 1;

        while(i>= 0 && s[i] == ' '){
            i --;
        }
        while(i>=0 && s[i] != ' '){
            length ++;
            i--;
        }
        return length;
    }
};
```
/---------------------------------------------------------------------------------------------------------------------------/
66. Plus One

You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.
Increment the large integer by one and return the resulting array of digits.

Example 1:
Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
Incrementing by one gives 123 + 1 = 124.
Thus, the result should be [1,2,4].

Constraints:
1 <= digits.length <= 100
0 <= digits[i] <= 9
digits does not contain any leading 0's.
```cpp
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
        int n = digits.size();

        for(int i=n-1; i>=0; --i){
            if(digits[i] < 9){
                digits[i]++;
                return digits;
            }
            digits[i] = 0;
        }
        digits.insert(digits.begin(),1);
        return digits;
    }
};
// we can use the condition like 'if digits[i] + 1 != 10 and if i == 0 
```
/---------------------------------------------------------------------------------------------------------------------------/

```cpp

```
/---------------------------------------------------------------------------------------------------------------------------/

```cpp

```
/---------------------------------------------------------------------------------------------------------------------------/

```cpp

```