# Top-100-most-asked-leetcode-questions-in-coding-interviews-


### Question 1
Arrays   Bit Manipulation

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
