## 167. Two Sum II - Input Array Is Sorted

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order, find two numbers such that they add up to a specific target number. Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.

Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.


```
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
         vector<int> ans;
         int start = 0, end = (numbers.size() - 1);
            while (start < end)
            {
                if ((numbers[start] + numbers[end]) > target) end--;
                else if ((numbers[start] + numbers[end]) < target) start++;
                else {
                    ans.push_back(++start); 
                    ans.push_back(++end);
                    break;
                };
            }
            return ans; 
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
