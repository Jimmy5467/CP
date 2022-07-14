## 105. Construct Binary Tree from Preorder and Inorder Traversal

Given two integer arrays preorder and inorder where preorder is the preorder traversal of a binary tree and inorder is the inorder traversal of the same tree, construct and return the binary tree.

```
class Solution {
    int findPosition(vector<int>& in, int element, int size){
        for(int i=0;i<size;i++){
            if(element == in[i])
                return i;
        }
        return -1;
    }
    TreeNode* solve(vector<int>& pre, vector<int>& in, int &index, int inOrederStart, int inOrderEnd, int n){
        if(index >= n || inOrederStart > inOrderEnd)
            return NULL;
        int element = pre[index++];
        TreeNode* root = new TreeNode(element);
        int position = findPosition(in,element,n);
        
        root->left = solve(pre, in, index, inOrederStart, position-1,n);
        root->right = solve(pre, in, index, position+1, inOrderEnd,n);
        return root;
    } 
public:
    TreeNode* buildTree(vector<int>& pre, vector<int>& in) {
        int preOrderIndex = 0, n = pre.size();
        TreeNode* ans = solve(pre, in, preOrderIndex, 0, n-1, n);
        return ans;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
