## 3. Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without repeating characters.

```
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
    int ans = 0;
        unordered_map<char, int> map;

        for(int i = 0, j = 0; j < s.size(); j++){
            if(map.find(s[j]) != map.end()){
                i = max(map[s[j]], i);
            }
            ans = max(ans, j - i + 1);
            map[s[j]] = j + 1;
        }

        return ans;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
