## 1473. Paint House III

There is a row of m houses in a small city, each house must be painted with one of the n colors (labeled from 1 to n), some houses that have been painted last summer should not be painted again.

A neighborhood is a maximal group of continuous houses that are painted with the same color.

For example: houses = [1,2,2,3,3,2,1,1] contains 5 neighborhoods [{1}, {2,2}, {3,3}, {2}, {1,1}].
Given an array houses, an m x n matrix cost and an integer target where:

houses[i]: is the color of the house i, and 0 if the house is not painted yet.
cost[i][j]: is the cost of paint the house i with the color j + 1.
Return the minimum cost of painting all the remaining houses in such a way that there are exactly target neighborhoods. If it is not possible, return -1.

```
class Solution {
public:
    int minCost(vector<int>& houses, vector<vector<int>>& cost, int m, int n, int target) {
        const int INF = 1e9;
        vector<vector<int>> dp(target + 1, vector<int> (n, INF));
        if (houses[0] == 0) {
            dp[1] = cost[0];
        } else {
            dp[1][houses[0] - 1] = 0;
        }
        
        for (int i = 1; i < m; i++) {
            for (int groups = target; groups > 0; groups--) {
                for (int color1 = 0; color1 < n; color1++) {
                    int min_cost = dp[groups][color1];
                    dp[groups][color1] = INF;
                    if (houses[i] != 0 && houses[i] != color1 + 1) continue;
                    int c = (houses[i] == 0) ? cost[i][color1] : 0;
                    min_cost += c;
                    for (int color2 = 0; color2 < n; color2++) {
                        if (color1 == color2) continue;
                        min_cost = min(min_cost, dp[groups - 1][color2] + c);
                    }
                    dp[groups][color1] = min_cost;
                }
            }
        }
        
        int ans = INF;
        for (int color = 0; color < n; color++) {
            ans = min(ans, dp[target][color]);
        }
        return (ans < INF ? ans : -1);
    }
};


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
```
