## 1658. Minimum Operations to Reduce X to Zero

You are given an integer array nums and an integer x. In one operation, you can either remove the leftmost or the rightmost element from the array nums and subtract its value from x. Note that this modifies the array for future operations.

Return the minimum number of operations to reduce x to exactly 0 if it is possible, otherwise, return -1.

```
class Solution {
public:
    int minOperations(vector<int>& nums, int x) {
      int total=0,n=nums.size();
        for(int num : nums)total+=num;
        int need=total-x,cur=0,longest=0;
        if(need==0)return n;
        int l=0,r=0;
        while(l<=r){
            if(cur<need){
                if(r<n)cur+=nums[r++];
                else break;
            }else if(cur>need){
                cur-=nums[l++];
            }else{
                longest=max(longest,r-l);
                cur-=nums[l++];
            }
        }
        if(cur==need)longest=max(longest,r-l);
        if(longest==0)return -1;
        return n-longest;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
