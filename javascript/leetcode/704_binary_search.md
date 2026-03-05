# Solution

```
var search = function(nums, target) {
    let min = 0;
    let max = nums.length -1;
    let mid = 0;

    while (min <= max) {
        let mid = Math.floor((min + max) / 2);
        let itemToCheck = nums[mid];

        if(itemToCheck === target) {
            return mid;
        }

        if (target > itemToCheck) {
            min = mid + 1;
        } else if (target < itemToCheck) {
            max = mid - 1;
        }
    }

    return -1;
};

```

# What to be cautious of

## length

I had tendency to constantly call length() method instead of using property length for Arrays / strings. Do not mess up with Python len() method.

- JS: [resource on Arrays.length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/length)
- JS: [resource on String.length](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length)
- Python: [resource on len()](https://www.w3schools.com/python/ref_func_len.asp)

# Step by step examples

## Array of [-1,0,3,5,9,12], we search for 9

**First iteration**

- min = 0, max = 5
- mid = Math.floor((0 + 5) / 2) = 2 // We need to use Matk.floor() in order to get integer number instead of float number
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
mid = Math.floor((0 + 5) / 2) = 2
nums[2] = 3
3 > 2, so our max now is 3 - 1 = 2;

**Second iteration**
min = 0, max = 2
mid = Math.floor((0 + 2) / 2) = 1;
nums[1] = 0;
0 < 2 so our new min is 1 + 1 = 2;

**Third iteration**
min = 2, max = 2
mid = Math.floor((2 + 2) / 2) = 2
nums[2] = 3
3>2, so new max is 2 - 1 = 1

min > max
2 > 1 - we return -1
