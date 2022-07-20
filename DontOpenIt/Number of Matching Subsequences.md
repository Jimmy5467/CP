## 792. Number of Matching Subsequences

Given a string s and an array of strings words, return the number of words[i] that is a subsequence of s.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

For example, "ace" is a subsequence of "abcde".
 
```
class Solution {
public:
    int numMatchingSubseq(string s, vector<string>& words) {
        vector<vector<int>> charMap(26);
        int n = s.length();
        
        for(int i = 0; i < n; i++) {
            charMap[s[i] - 'a'].push_back(i);
        }
        
        int ans = words.size();
        
        for(auto& word : words) {
            int last = -1;
            
            for(char c : word) {
                auto& cIndexes = charMap[c - 'a'];
                auto it = upper_bound(cIndexes.begin(), cIndexes.end(), last);
                if(it == cIndexes.end()) {
                    ans--;
                    break;
                } else {
                    last = *it;
                }
            }
        }
        
        return ans;
    }
}; 
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
