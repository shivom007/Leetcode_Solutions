#[2149. Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/description/)


## Solution
      <!-- C++ Brute force -->

      class Solution {
      public:
        vector<int> rearrangeArray(vector<int>& nums) {
             vector<int> ans;
             int n = nums.size();
             list<int> pve;
             list<int> nve;
     
             for(int &x : nums){
                 if(x > 0) pve.push_back(x);
                 else nve.push_back(x);
             }
             for(int i = 0; i < n; i++){
                 if(i % 2 == 0){
                      ans.push_back(pve.front());
                      pve.pop_front();
                 }
                 else {
                     ans.push_back(nve.front());
                     nve.pop_front();
                 }
             }
        return ans;
       }     
    };

    <!-- C++ Optimal -->

    class Solution {
      public:
       vector<int> rearrangeArray(vector<int>& nums) {
        vector<int> ans(nums.size());
        int i = 0, j = 1;
        for (int num : nums) {
            if (num > 0) {
                ans[i] = num;
                i += 2;
            } else {
                ans[j] = num;
                j += 2;
            }
        }
        return ans;
      }
    };