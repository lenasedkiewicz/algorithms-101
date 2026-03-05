# Solution

```
class Solution {
    public int search(int[] nums, int target) {
        int min = 0;
        int max = nums.length - 1;

        while (min <= max) {
            int mid = (min + max) / 2;
            int guess = nums[mid];
            if (guess == target) {
                return mid;
            }

            if (guess > target) {
                max = mid - 1;
            } else {
                min = mid + 1;
            }
        }
        return -1;
    }
}

```

# Step by step examples

## Array of [-1,0,3,5,9,12], we search for 9

**First iteration**

- min = 0, max = 5
- mid = (0 + 5) / 2 = 2 (when type in Java is int division returns integer)
- nums[2] = 3
- 3 < 9 so we move right: min = 3

**Second iteration**

- min = 3, max = 5
- mid = ( 3 + 5) / 2 = 4
- nums[4] = 9
- 9 = 9 --> we found it!
- return 4

## Array of [-1,0,3,5,9,12], we search for 2

**First iteration**
min = 0; max = 5
mid = (0 + 5) / 2 = 2
nums[2] = 3
3 > 2, so our max now is 3 - 1 = 2;

**Second iteration**
min = 0, max = 2
mid = (0 + 2) / 2 = 1;
nums[1] = 0;
0 < 2 so our new min is 1 + 1 = 2;

**Third iteration**
min = 2, max = 2
mid = (2 + 2) / 2 = 2
nums[2] = 3
3>2, so new max is 2 - 1 = 1

min > max
2 > 1 - we return -1
