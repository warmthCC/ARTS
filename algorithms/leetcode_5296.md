# 5296 [两棵二叉搜索树中的所有元素](https://leetcode-cn.com/problems/all-elements-in-two-binary-search-trees/)

## description

给你 root1 和 root2 这两棵二叉搜索树。

请你返回一个列表，其中包含 两棵树 中的所有整数并按 升序 排序。.

示例 1：

```
输入：root1 = [2,1,4], root2 = [1,0,3]
输出：[0,1,1,2,3,4]
```

示例 2：

```
输入：root1 = [0,-10,10], root2 = [5,1,7,0,2]
输出：[-10,0,0,1,2,5,7,10]
```

示例 3：

```
输入：root1 = [], root2 = [5,1,7,0,2]
输出：[0,1,2,5,7]
```

示例 4：

```
输入：root1 = [0,-10,10], root2 = []
输出：[-10,0,10]
```

示例 5：

```
输入：root1 = [1,null,8], root2 = [8,1]
输出：[1,1,8,8]
```

提示：

每棵树最多有 5000 个节点。
每个节点的值在 [-10^5, 10^5] 之间。

## my solution

```c++
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
    vector<int> getAllElements(TreeNode* root1, TreeNode* root2) {
        vector<int> result;
        stack<TreeNode*> l,r;
        TreeNode* cur1 = root1;
        TreeNode* cur2 = root2;
        while (cur1 || cur2 || !l.empty() || !r.empty()) {
            while (cur1) {
                l.push(cur1);
                cur1 = cur1->left;
            }
            while (cur2) {
                r.push(cur2);
                cur2 = cur2->left;
            }
            if (r.empty() || (!l.empty() && !r.empty() && l.top()->val <= r.top()->val)){
                cur1 = l.top();
                l.pop();
                result.push_back(cur1->val);
                cur1 = cur1->right;
            } else {
                cur2 = r.top();
                r.pop();
                result.push_back(cur2->val);
                cur2 = cur2->right;
            }
        }
        return result;
    }
};
```

## time and space complexity

T(N) = O(N)
S(N) = O(N)

N:两棵🌲总节点数

## others

我挺喜欢自己这个解法的哈哈哈哈
