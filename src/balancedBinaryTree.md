#### Balanced Binary Tree
Leetcode question #110</br>
Technique use: DFS
```
class Solution {
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        if (Math.abs(getDepth(root.left) - getDepth(root.right)) > 1) return false;
        return isBalanced(root.left) && isBalanced(root.right);
    }
    
    public int getDepth(TreeNode node) {
        if (node == null) return 0;
        return 1 + Math.max(getDepth(node.left), getDepth(node.right));
    }
}

class Solution2 {
    public boolean isBalanced(TreeNode root) {
        if (root == null) return true;
        return getDepth(root) != -1;
    }
    
    public int getDepth(TreeNode root) {
        if (root == null) return 0;
        int left = getDepth(root.left);
        int right = getDepth(root.right);
        if (left == -1 || right == -1) {
            return -1;
        }
        if (Math.abs(left - right) > 1) return -1;
        return 1 + Math.max(left, right);
    }
}
```