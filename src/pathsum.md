#### Path Sum
Leetcode question #112, #113</br>
Technique use: DFS

##### Path sum I
```
class Solution {
    public boolean hasPathSum(TreeNode root, int sum) {
        if (root == null) return false;
        sum -= root.val;
        if (root.right == null && root.left == null && sum == 0) return true;
        return hasPathSum(root.right, sum) || hasPathSum(root.left, sum);
    }
}
```


##### Path sum II
```
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> paths = new ArrayList<>();
        Stack<Integer> stack = new Stack<>();
        pathSum(root, sum, paths, stack);
        return paths;
    }
    
    public void pathSum (TreeNode root, int sum, List<List<Integer>> paths, Stack<Integer> stack) {
        if (root == null) return;
        stack.push(root.val);
        sum -= root.val;
        if (root.left == null && root.right == null && sum == 0) paths.add(new ArrayList<>(stack));
        pathSum(root.left, sum, paths, stack);
        pathSum(root.right, sum, paths, stack);
        stack.pop();
    }
}
```
