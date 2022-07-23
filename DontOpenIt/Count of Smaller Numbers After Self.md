## 315. Count of Smaller Numbers After Self

You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].

```
class Solution
{
    public:
    vector<int> res;
    vector<pair<int, int>> arr;
    
    void solve(int low, int high, int low1, int high1)
    {
        int i = low, c = 0;
        vector<pair<int, int>> vec;
        while (low <= high && low1 <= high1)
        {
            if (arr[low1].first >= arr[low].first) vec.push_back(arr[low1++]);
            else
            {
                vec.push_back(arr[low]);
                res[arr[low++].second] += high1 - low1 + 1;
            }
        }
        while (low <= high) vec.push_back(arr[low++]);
        while (low1 <= high1) vec.push_back(arr[low1++]);
        for (auto j: vec) arr[i++] = j;
    }
    
    void merge(int low, int high)
    {
        if (low == high) return;
        int mid = (low + high) / 2;
        if (low != mid) merge(low, mid);
        if (mid + 1 != high) merge(mid + 1, high);
        solve(low, mid, mid + 1, high);
    }
    
    vector<int> countSmaller(vector<int> &nums)
    {
        int n = nums.size();
        res.clear();
        res.resize(n, 0);
        arr.clear();
        for (int i = 0; i < n; i++)
        {
            arr.push_back(make_pair(nums[i], i));
        }
        merge(0, n - 1);
        return res;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
