## 890. Find and Replace Pattern

Given a list of strings words and a string pattern, return a list of words[i] that match pattern. You may return the answer in any order.

A word matches the pattern if there exists a permutation of letters p so that after replacing every letter x in the pattern with p(x), we get the desired word.

Recall that a permutation of letters is a bijection from letters to letters: every letter maps to another letter, and no two letters map to the same letter.

```
class Solution {
public:
    vector<string> findAndReplacePattern(vector<string>& words, string pattern) {
        vector<string> ans;
        for(string s : words){
           
            if(s.size()!=pattern.size())continue;
           
            vector<char> arr(26,NULL);
            unordered_map<char,int> hm;
            bool flag = true;
            
            for(int j = 0;j<s.size();j++){
                char a = s[j];
                char b = pattern[j];
              
                if((arr[a-'a']==NULL && hm.count(b)==0)||arr[a-'a']== b) {
                    arr[a-'a'] = b;
                    hm[b] = 1;
                }
                else{
                   flag = false;
                    break;
                } }
            
            if(flag ){
                ans.push_back(s);
            }
            
        }
        
        return ans;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
