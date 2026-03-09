# 35 Search Insert Position - Objective

If target exists, we return it's index. If not, we return index where it would be if it was to be inserted

# Solution

```
var searchInsert = function(nums, target) {
    let min = 0;
    let max = nums.length - 1;

    while (min <= max) {
        let mid = Math.floor((min + max) / 2);

        if (nums[mid] === target) {
            return mid;
        }

        if (target < nums[mid]) {
            max = mid - 1;
        } else {
            min = mid + 1
        }
    }

    return min;
};
```

# Step by step examples
