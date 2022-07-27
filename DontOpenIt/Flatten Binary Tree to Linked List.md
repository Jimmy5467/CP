## 114. Flatten Binary Tree to Linked List


Given the root of a binary tree, flatten the tree into a "linked list":

The "linked list" should use the same TreeNode class where the right child pointer points to the next node in the list and the left child pointer is always null.
The "linked list" should be in the same order as a pre-order traversal of the binary tree.


```
class Solution {
public:
    void flatten(TreeNode* root) {
     if(root == NULL) return;
        TreeNode *Left = root->left;
        TreeNode *Right = root->right;
		
        root->left = NULL;
		
        flatten(Left);
        flatten(Right);
        root->right = Left;
        TreeNode *curr = root;
		
        while(curr->right != NULL) curr = curr->right;		
        curr->right = Right;   
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.

