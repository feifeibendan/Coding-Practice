#### 3 Sum
Leetcode question #15</br>
Technique use: Two pointer
```
public List<List<Integer>> threeSum(int[] nums) {        
    Arrays.sort(nums); //array here must be sorted inorder to use two pointer
    List<List<Integer>> ansList = new ArrayList<>();
    for (int i = 0; i < nums.length - 2; i++) {
        int head = i + 1, tail = nums.length - 1;
        while (head < tail) {
            int val = nums[i] + nums[head] + nums[tail];
            if (val == 0) {
                ansList.add(Arrays.asList(nums[i], nums[head], nums[tail]));
                while (i + 1 < nums.length && nums[i] == nums[i+1]) i++;
                while (head < tail && nums[head] == nums[head + 1]) head++;
                while (head < tail && nums[tail] == nums[tail - 1]) tail--;
                tail--; //order matter here
                head++; //if this in the front, case [-2, 0, 1, 1, 2] does not work
            } else if (val > 0) {
                tail--;    
            } else {
                head++;
            }
        }
    }
    return ansList;
}
```