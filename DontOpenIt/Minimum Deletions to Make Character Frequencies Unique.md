## 1647. Minimum Deletions to Make Character Frequencies Unique

A string s is called good if there are no two different characters in s that have the same frequency.

Given a string s, return the minimum number of characters you need to delete to make s good.

The frequency of a character in a string is the number of times it appears in the string. For example, in the string "aab", the frequency of 'a' is 2, while the frequency of 'b' is 1.

```
class Solution {
public:
    int minDeletions(string s) {
        int n=s.size();
        unordered_map<char,int>mp;
        for(int i=0;i<n;i++)
            mp[s[i]]++;
        int ans=0;
        set<int>st;
        for (auto[i,j] :mp){
            while(st.find(j)!=st.end()){
                j--;
                ans++;
            }   
            if(j>0)
                st.insert(j); 
        }
        return ans;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
