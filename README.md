# Top-100-most-asked-leetcode-questions-in-coding-interviews-


### Question 1
Arrays,Bit Manipulation

Question:
**[Missing Number](https://leetcode.com/problems/missing-number/description/)**

**Companies:** Amazon,Apple,Google,Microsoft,Bloomberg,Uber,Facebook,Adobe,tcs,Yahoo

Solution:
```class Solution {
public:
    int missingNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int n=nums.size();
        for(int i=0;i<n;i++){
            if(nums[i]!=i){
                return i;
            }
        }
        return n;
    }
};
```
### Question 2
Array,Hash Table

Question:
**[First Missing Positive](https://leetcode.com/problems/first-missing-positive/description/)**

**Companies:** Amazon

Solution:
```class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        int i;
        set<int> st;
        for(i=0;i<nums.size();i++){
            st.insert(nums[i]);
        }        
        i=1;
        while(i<=st.size()){
            if(st.find(i)!=st.end())i++;
            else return i;
        }
        return i;

    }
};
```

### Question 3
Array,Hash Table

Question:
**[Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/description/)**

**Companies:** Facebook

Solution:
```class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int> ans;
        unordered_map<int,int> m;
        for(int x:nums) m[x]++;
        for(int i=1;i<=nums.size();i++)
        {
            if(m[i]==0) ans.push_back(i); 
        }
        return ans;

    }
};
```

### Question 4
Array,Map,Bit Manipulation

Question:
**[Single Number](https://leetcode.com/problems/single-number/description/)
**
**Companies:** Google,Amazon,Apple,Bloomberg,Adobe,Zoho,Yandex,Yahoo

Solution:
#### Bit Manipulation
```class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int n;
        int ans=0;
        n=nums.size();
        for(int i=0;i<n;i++){
            ans^=nums[i];
        }
        return ans;

    }
};
```
#### Map
```class Solution {
public:
    int singleNumber(vector<int>& nums) {
        unordered_map<int,int> mp;
        for(int i=0;i<nums.size();i++){
            mp[nums[i]]++;
        }
        for(auto m:mp){
            if(m.second==1){
                return m.first;
            }
        }
        return -1;
    }
};
```
### Question 5
Dynamic Programming

Question:
**[Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)**
**Companies:** 	
Amazon,Google,Adobe,Bloomberg,Yahoo,Zoho,Apple,Microsoft,Uber,Swiggy,Accenture,Qualcomm,Nagarro
Solution:
####Approach 1: Recursion 
Explanation: The recursive solution uses the concept of Fibonacci numbers to solve the problem. It calculates the number of ways to climb the stairs by 
recursively calling the climbStairs function for (n-1) and (n-2) steps. However, this solution has exponential time complexity (O(2^n)) due to redundant 
calculations.
```class Solution {
public:
    int climbStairs(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        return climbStairs(n-1) + climbStairs(n-2);
    }
};
```
####Approach 2: Memoization
Explanation: The memoization solution improves the recursive solution by introducing memoization, which avoids redundant calculations. We use an unordered map 
(memo) to store the already computed results for each step n. Before making a recursive call, we check if the result for the given n exists in the memo. If it 
does, we return the stored value; otherwise, we compute the result recursively and store it in the memo for future reference.
```class Solution {
public:
    int climbStairs(int n, unordered_map<int, int>& memo) {
        if (n == 0 || n == 1) {
            return 1;
        }
        if (memo.find(n) == memo.end()) {
            memo[n] = climbStairs(n-1, memo) + climbStairs(n-2, memo);
        }
        return memo[n];
    }

    int climbStairs(int n) {
        unordered_map<int, int> memo;
        return climbStairs(n, memo);
    }
};
```
####Approach 3: Tabulation
Explanation: The tabulation solution eliminates recursion and uses a bottom-up approach to solve the problem iteratively. It creates a DP table (dp) of size n+1 
to store the number of ways to reach each step. The base cases (0 and 1 steps) are initialized to 1 since there is only one way to reach them. Then, it iterates 
from 2 to n, filling in the DP table by summing up the values for the previous two steps. Finally, it returns the value in the last cell of the DP table, which 
represents the total number of ways to reach the top.
```class Solution {
public:
    int climbStairs(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }

        vector<int> dp(n+1);
        dp[0] = dp[1] = 1;
        
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i-1] + dp[i-2];
        }
        return dp[n];
    }
};
```
