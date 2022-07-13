## 102. Binary Tree Level Order Traversal

Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

```
class Solution {
public:
    vector<vector<int>> ans;
    void help(TreeNode* root, int level){
        if(root == NULL){
            return;
        }
        if(ans.size()<=level){
            vector<int> temp{root->val};
            ans.push_back(temp);
        }
        else{
            ans[level].push_back(root->val);
        }
        help(root->left,level+1);        
        help(root->right,level+1);
    }
    vector<vector<int>> levelOrder(TreeNode* root) {
        help(root, 0);
        return ans;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
