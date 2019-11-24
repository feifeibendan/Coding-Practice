#### 34 Find First and Last Position of Element in Sorted Array
Leetcode question #34</br>
Technique use: binary search
```
class Solution {
    public int[] searchRange(int[] nums, int target) {
        if (nums.length == 0) return new int[]{-1, -1};
        int l = leftIndex(nums, target);
        if (l== nums.length || nums[l] != target) return new int[]{-1, -1};
        int r = rightIndex(nums, target);
        return new int[]{l, r};
    }
    
    public int leftIndex(int[] nums, int target) {
        int l = 0, r = nums.length -1;
        while (l <= r) {
            int m = l + (r - l) / 2;
            if (nums[m] < target) {
                l = m +1;
            } else {
                r = m -1;
            }
        }
        return l;
    }
    
    public int rightIndex(int[] nums, int target) {
        int l = 0, r = nums.length -1;
        while (l <= r) {
            int m = l + (r - l) / 2;
            if (nums[m] <= target) {
                l = m + 1;
            } else {
                r = m -1;
            }
        }
        return l-1;
    }
}
```