## 745. Prefix and Suffix Search

Design a special dictionary with some words that searchs the words in it by a prefix and a suffix.

Implement the WordFilter class:

WordFilter(string[] words) Initializes the object with the words in the dictionary.
f(string prefix, string suffix) Returns the index of the word in the dictionary, which has the prefix prefix and the suffix suffix. If there is more than one valid index, return the largest of them. If there is no such word in the dictionary, return -1.

```
class WordFilter {
public:
    unordered_map<string,int>um;
    WordFilter(vector<string>& words) {
        for(int k=0;k<words.size();k++)
        {
            string word=words[k];
            int l=word.size();
            for(int i=0;i<l;i++)
            {
                for(int j=l-1;j>=0;j--)
                {
                    um[word.substr(0,i+1)+'|'+word.substr(j)]=k;
                }
            }
        }
    }
    
    int f(string prefix, string suffix) {
        if(um.find(prefix+'|'+suffix)==um.end())
        {
            return -1;
        }
        return um[prefix+'|'+suffix];
    }
};

/**
 * Your WordFilter object will be instantiated and called as such:
 * WordFilter* obj = new WordFilter(words);
 * int param_1 = obj->f(prefix,suffix);
 */
  ```
  
If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
