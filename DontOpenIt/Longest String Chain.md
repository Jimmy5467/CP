## 1048. Longest String Chain

You are given an array of words where each word consists of lowercase English letters.

wordA is a predecessor of wordB if and only if we can insert exactly one letter anywhere in wordA without changing the order of the other characters to make it equal to wordB.

For example, "abc" is a predecessor of "abac", while "cba" is not a predecessor of "bcad".
A word chain is a sequence of words [word1, word2, ..., wordk] with k >= 1, where word1 is a predecessor of word2, word2 is a predecessor of word3, and so on. A single word is trivially a word chain with k == 1.

Return the length of the longest possible word chain with words chosen from the given list of words.

```
class Solution {
public:
    int longestStrChain(vector<string>& words) {
        vector<unordered_set<string>> W(17);
        for (auto word : words) 
            W[word.size()].insert(word);
        unordered_map<string, int> dp;
        int best = 1;
        for (int i = 16; i; i--) {
            if (W[i-1].empty()) continue;
            for (auto word : W[i]) {
                int wVal = dp[word] ? dp[word] : 1;
                for (int j = 0; j < word.size(); j++) {
                    string pred = word.substr(0,j) + word.substr(j+1);
                    int pVal = dp[pred] ? dp[pred] : 1;
                    if (W[i-1].find(pred) != W[i-1].end() && wVal >= pVal) {
                        dp[pred] = wVal + 1;
                        best = max(best, wVal + 1);
                    }
                }
            }
        }
        return best;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.

