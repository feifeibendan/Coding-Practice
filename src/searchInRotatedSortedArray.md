#### 33 Search In Rotated Sorted Array
Leetcode question #33</br>
Technique use: Binary Search
```
public int search(int[] nums, int target) {
    if (nums.length == 0) return -1;
    int l = 0, r = nums.length - 1;
    while (l <= r) {
        int m = l + (r - l) / 2;
        if (nums[m] == target) {
            return m;
        }
        if (nums[m] >= nums[l]) {   //careful here, side matter here, 
            if (nums[l] <= target && nums[m] > target) {
                r = m - 1;
            } else {
                l = m + 1;
            } 
        } else {
            if (nums[m] < target && nums[r] >= target) {
                l = m +1;
            } else {
                r = m - 1;
            }
        }
    }
    return -1;
}
```