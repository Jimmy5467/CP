## 1696. Jump Game VI

You are given a 0-indexed integer array nums and an integer k.

You are initially standing at index 0. In one move, you can jump at most k steps forward without going outside the boundaries of the array. That is, you can jump from index i to any index in the range [i + 1, min(n - 1, i + k)] inclusive.

You want to reach the last index of the array (index n - 1). Your score is the sum of all nums[j] for each index j you visited in the array.

Return the maximum score you can get.

```
class Solution {
public:
    int maxResult(vector<int>& nums, int k) {
         int n=nums.size();
        int score[n];
        priority_queue<pair<int, int>> pq;
        
        for(int i=n-1 ; i>=0 ; i--)
        {
            while(pq.size() && pq.top().second>i+k)
                pq.pop();
            
            score[i]=nums[i];
            score[i]+=(pq.size() ? pq.top().first : 0);
            pq.push({score[i], i});
        }
        
        return score[0];
    }
}; 
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
