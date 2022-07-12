## 473. Matchsticks to Square

You are given an integer array matchsticks where matchsticks[i] is the length of the ith matchstick. You want to use all the matchsticks to make one square. You should not break any stick, but you can link them up, and each matchstick must be used exactly one time.

Return true if you can make this square and false otherwise.

``` 
class Solution {
public:
    bool solve(int idx, vector <int>& sums, int target, vector <int>& matchsticks){
        if(idx >= matchsticks.size()){
            return sums[0] == sums[1] && sums[1] == sums[2] && sums[2] == target;
        }
        for(int i = 0; i < 4; i++){
            if(sums[i] + matchsticks[idx] > target)continue;
            sums[i] += matchsticks[idx];
            if(solve(idx + 1, sums, target, matchsticks)) return true;
            sums[i] -= matchsticks[idx];
        }
         return false;
   }
    bool makesquare(vector<int>& matchsticks) {
        if(matchsticks.size() == 0) return false;
        int x = 0;
        for(int i = 0; i < matchsticks.size(); i++){
           x += matchsticks[i];
        }
        if(x % 4) return false;
        sort(matchsticks.rbegin(), matchsticks.rend());
        vector <int> sum(4);
        return solve(0, sum,x / 4, matchsticks);
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
