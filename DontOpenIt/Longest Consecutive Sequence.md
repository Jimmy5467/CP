## 128. Longest Consecutive Sequence

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

```
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int max_len = 0;
        unordered_set<int> num_set(nums.begin(), nums.end());
        for (int num : nums) {
            if (num_set.find(num - 1) == num_set.end()) {
                int curr_num = num;
                int curr_len = 1;
                while (num_set.find(curr_num + 1) != num_set.end()) {
                    curr_num++;
                    curr_len++;
                }
                max_len = max(max_len, curr_len);
            }
        }
        return max_len;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
