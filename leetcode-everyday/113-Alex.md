# Leetcode 113. 路径总和2

给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

说明: 叶子节点是指没有子节点的节点。

示例:
给定如下二叉树，以及目标和 sum = 22，

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
返回:

[
   [5,4,11,2],
   [5,8,4,5]
]





```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>>ret;
    vector<int> path;
    void dfs(TreeNode*root,int sum){//深度优先搜索，遍历每一条符合条件的路径
        if(root==NULL){
            return ;
        }
        path.push_back(root->val);
        sum-=root->val;
        if(root->left==NULL&&root->right==NULL&&sum==0){
            ret.push_back(path);//将符合条件的路径加入结果表示中
        }
        dfs(root->left,sum);
        dfs(root->right,sum);
        // path.pop_back(ret);
        path.pop_back();

    }
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        dfs(root,sum);
        return ret;
    }
};
```

