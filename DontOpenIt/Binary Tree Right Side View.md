## 199. Binary Tree Right Side View

Given the root of a binary tree, imagine yourself standing on the right side of it, return the values of the nodes you can see ordered from top to bottom.

```
class Solution {
public:
    vector<int> solve(TreeNode* root, vector<int> k, int lvl){
        if (root==NULL){
            return k;
        }
        if (k.size()==lvl){                 // root
            k.push_back(root->val);
        }
        k = solve(root->right , k , lvl + 1);     // right
        k = solve(root->left , k , lvl + 1);       // left
        return k;
    }
    
    vector<int> rightSideView(TreeNode* root) {
        vector<int> k;
        k = solve( root , k , 0 );
        return k;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
