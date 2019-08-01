#### Find next greater element
Leetcode question #496</br>
Technique use: Brutal force (Need to improve)

```
public int[] nextGreaterElement(int[] nums1, int[] nums2) {
    int[] ans = new int[nums1.length];
    for (int i = 0; i < nums1.length; i++) {
        ans[i] = -1;
    }
        
    for (int i = 0; i < nums1.length; i++) {
        boolean found = false;
        for (int j = 0; j < nums2.length; j++) {
            if (!found && nums1[i] == nums2[j]) {
                found = true;
            } 
            if (found && j < nums2.length - 1 && nums1[i] < nums2[j + 1]) {
                ans[i] = nums2[j + 1];
                break;
            }
        }
    }
    return ans;
}
```