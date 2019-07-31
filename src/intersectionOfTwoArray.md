#### Intersection of two array II
Leetcode question #350</br>
Technique use: 

```
public int[] intersect(int[] nums1, int[] nums2) {
    Map<Integer, Integer> map = new HashMap<>();
    for (Integer num : nums1) {
        map.put(num, map.getOrDefault(num, 0) + 1);
    }
    List<Integer> list = new ArrayList<>();
    for (Integer num : nums2) {
        if (map.getOrDefault(num, 0) > 0) {
            list.add(num);
            map.put(num, map.get(num) - 1);
        }
    }
    int[] ans = new int[list.size()];
    for (int i = 0; i < list.size(); i++) {
        ans[i] = list.get(i);
    }
    return ans;
}
```