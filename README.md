# leetcode
My leetcode solutions in java

## Two Sum
```java
var containsDuplicate = function(nums) {
    const seen = {};

    for (let num of nums) {
        if (seen[num]) {
            return true
        } else {
            seen[num] = true;
        }
    }

    return false;
}
```
