# leetcode
My leetcode solutions in java

## Two Sum
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] returnArray = new int[2];
        for (int i = 0; i < nums.length - 1; i ++ ) {
            for (int j = 1; j < nums.length; j ++ ) {
                if (i == j) {
                    continue;
                }
                if (nums[i] + nums[j] == target) {
                    returnArray[0] = i;
                    returnArray[1] = j;
                    return returnArray;
                }
            }
        }
        
        return returnArray;
    }
}
```
