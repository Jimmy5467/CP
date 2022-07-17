## 629. K Inverse Pairs Array

For an integer array nums, an inverse pair is a pair of integers [i, j] where 0 <= i < j < nums.length and nums[i] > nums[j].
Given two integers n and k, return the number of different arrays consist of numbers from 1 to n such that there are exactly k inverse pairs. Since the answer can be huge, return it modulo 109 + 7.

```
const int mod = 1e9 + 7, N = 1010;

class Solution {
    int f[N][N] = {};
public:
    int kInversePairs(int n, int K) {
        f[0][0] = 1;
        for (int i = 1; i <= n; ++ i) // 1000
        {
            long long s = 0; // maintain a window that is length min(i, j);
            for (int j = 0; j <= K; ++ j) // 1000
            {
                s += f[i - 1][j];
                if (j >= i)
                    s -= f[i - 1][j - i];
                f[i][j] = ((long long)f[i][j] + s) % mod; 
            }
        }
        return f[n][K];
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
