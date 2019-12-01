#### 78 Subsets
Leetcode question #78</br>
Technique use: 
Iteration
```
public class Solution {
    public List<List<Integer>> subsets(int[] nums) { 
        Arrays.sort(nums);   
        List<List<Integer>> ans = new ArrayList<>();
        ans.add(new ArrayList<>());
        for (int i = 0; i < nums.length; i++) {
            int size = ans.size();
            for (int j = 0; j < size; j++) {
                List<Integer> list = new ArrayList<>(ans.get(j));
                list.add(nums[i]);
                ans.add(list);
            }
        }
        return ans;
    }
}
```

DFS
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ans = new ArrayList<>();
        DFSHelper(ans, new ArrayList<>(), nums, 0);
        return ans;
    }
    
    public void DFSHelper(List<List<Integer>> ans, List<Integer> list, int[] nums, int start) {
        if (start <= nums.length) {
            ans.add(list);
        }
        for (int i = start; i < nums.length; i++) {
            list.add(nums[i]);
            DFSHelper(ans, new ArrayList<>(list), nums, i + 1);
            list.remove(list.size() - 1);
        }
    }
}
```