##34. Find First and Last Position of Element in Sorted Array

Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

```
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
         auto low = lower_bound(nums.begin(),nums.end(),target);
        auto up = upper_bound(nums.begin(),nums.end(),target);
        
        if(low == nums.end() || *low != target)    return {-1,-1};
        
        int first = low - nums.begin();
        int last = up - nums.begin()-1;
        
        return {first ,last};
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
