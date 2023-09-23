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

### Question 3
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
