## 1268. Search Suggestions System

You are given an array of strings products and a string searchWord.

Design a system that suggests at most three product names from products after each character of searchWord is typed. Suggested products should have common prefix with searchWord. If there are more than three products with a common prefix return the three lexicographically minimums products.

Return a list of lists of the suggested products after each character of searchWord is typed.


```
class Solution {
public:
    vector<vector<string>> suggestedProducts(vector<string>& products, string searchWord) {
        sort(products.begin(), products.end());
        vector<vector<string>> ans;
        int left = 0, right = products.size() - 1;
        for (int i = 0; i < searchWord.length(); i++) {
            vector<string> res;
            char c = searchWord[i];
            while (left <= right && (products[left].length() == i || products[left][i] < c)) left++;
            while (left <= right && (products[right].length() == i || products[right][i] > c)) right--;
            for (int j = 0; j < 3 && left + j <= right; j++)
                res.push_back(products[left+j]);
            ans.push_back(res);
        }
        return ans;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
