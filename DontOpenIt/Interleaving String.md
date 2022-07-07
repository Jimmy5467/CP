## 97. Interleaving String

Given strings s1, s2, and s3, find whether s3 is formed by an interleaving of s1 and s2.

An interleaving of two strings s and t is a configuration where they are divided into non-empty substrings such that:

s = s1 + s2 + ... + sn
t = t1 + t2 + ... + tm
|n - m| <= 1
The interleaving is s1 + t1 + s2 + t2 + s3 + t3 + ... or t1 + s1 + t2 + s2 + t3 + s3 + ...
Note: a + b is the concatenation of strings a and b.

```
class Solution {
public:
    bool isInterleave(string s1, string s2, string s3) {
        if (s1.length() + s2.length() != s3.length()) return false;
		if (s1.length() < s2.length()) swap(s1, s2);
		int m = s1.length(), n = s2.length();
			
        vector<bool> dp(n + 1, false);
        dp[0] = true;
        for (int j = 1; j <= n; j++) {
            dp[j] = s3[j - 1] == s2[j - 1] && dp[j - 1];
        }

        for (int i = 1; i <= m; i++) {
            dp[0] = s3[i - 1] == s1[i - 1] && dp[0];
            for (int j = 1; j <= n; j++) {
                dp[j] = (s3[i + j - 1] == s1[i - 1] && dp[j]);
                dp[j] = dp[j] || (s3[i + j - 1] == s2[j - 1] && dp[j - 1]);
            }
        }
        return dp.back();
    }
};
```



If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
