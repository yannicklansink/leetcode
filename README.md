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


## Valid Anagram
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        
        if (s.length() != t.length()) {
            return false;
        }
        
        char[] word = new char[s.length()];
        char[] wordToCompare = new char[t.length()];
    
        for (int i = 0; i < s.length(); i++) {
            word[i] = s.charAt(i);
        }
        for (int i = 0; i < t.length(); i++) {
            wordToCompare[i] = t.charAt(i);
        }
        
        boolean valid = false;
        for (int i = 0; i < word.length; i++) {
            valid = false;
            for (int j = 0; j < wordToCompare.length; j++) {
                if (word[i] == wordToCompare[j]) {
                    System.out.println("hey");
                    valid = true;      
                    wordToCompare[j] = ' ';
                    break;
                }
            }
            if (!valid) {
                return false;
            }
        }
        return true;
    }
}
```


 ## Contains Duplicate

```java
public boolean containsDuplicate(int[] nums) {
    Set<Integer> set = new HashSet<Integer>();
		 for(int i : nums)
			 if(!set.add(i))
				 return true; 
		 return false;
}
```

## Valid Palindrome
```java
public boolean isPalindrome(String s) {
        String newS = s.replaceAll("[^a-zA-Z0-9]", "");
        StringBuilder reversedS = new StringBuilder();
        reversedS.append(newS.toLowerCase());
        reversedS.reverse();
        return reversedS.toString().equals(newS.toLowerCase()) ? true : false;
    }
```
## Valid Parentheses
```java
public boolean isValid(String s) {
        
        Stack<Character> stack = new Stack<Character>();
        // Iterate through string until empty
        for(int i = 0; i<s.length(); i++) {
            // Push any open parentheses onto stack
            if(s.charAt(i) == '(' || s.charAt(i) == '[' || s.charAt(i) == '{')
                stack.push(s.charAt(i));
            // Check stack for corresponding closing parentheses, false if not valid
            else if(s.charAt(i) == ')' && !stack.empty() && stack.peek() == '(')
                stack.pop();
            else if(s.charAt(i) == ']' && !stack.empty() && stack.peek() == '[')
                stack.pop();
            else if(s.charAt(i) == '}' && !stack.empty() && stack.peek() == '{')
                stack.pop();
            else
                return false;
        }
        // return true if no open parentheses left in stack
        return stack.empty();
       
        
    }
```
## Best time to buy and sell stock
```java
public int maxProfit(int[] prices) {
        int buy=Integer.MAX_VALUE,sell=0;
        for(int i=0;i<prices.length;i++){
            buy=Math.min(buy,prices[i]);
            sell=Math.max(sell,prices[i]-buy);
        }
        return sell;
}
```
