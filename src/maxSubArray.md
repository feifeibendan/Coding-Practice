#### Max Subarray
Leetcode question #53</br>
Technique use: Kadane’s Algorithm

```
public int maxSubArray(int[] nums) {
    int max = Integer.MIN_VALUE, sum = 0;
    for (int num : nums) {
        sum += num;
        max = Math.max(max, sum);
        if (sum < 0) sum = 0;
    }
    return max;
}
```