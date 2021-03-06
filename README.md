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
## Binary Search
Spliting the array in half every loop run. O(log n)
```java
public int search(int[] nums, int target) {
        if (nums == null || nums.length == 0) return -1;
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            if (nums[mid] > target) right = mid - 1;
            else left = mid + 1;
        }
        return -1;
}
```
## Reverse Linked List
iteratively
```java 
public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        ListNode next = null;
        while (curr != null) {
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;    
        }
        return prev;
}
```  
## Merge 2 Sorted Linked List
https://leetcode.com/problems/merge-two-sorted-lists/submissions/
recursively
```java
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if(l1 == null) return l2;
        if(l2 == null) return l1;
        
        if(l1.val < l2.val){
            l1.next = mergeTwoLists(l1.next, l2);
            return l1;
        }
        else{
            l2.next = mergeTwoLists(l1, l2.next);
            return l2;
        }
}
```   
## Min Stack
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time. <br/>
Medium <br/>
https://leetcode.com/problems/min-stack/ <br/>
![image](https://user-images.githubusercontent.com/76790689/178001083-5bd6afd5-1021-48b5-b7ab-d03ab3483cd0.png)
![image](https://user-images.githubusercontent.com/76790689/178001106-7344f073-f1f9-48b0-8329-1a908a854c2d.png)


```java
class MinStack {
    
    private Node head;
        
    public void push(int x) {
        if (head == null) 
            head = new Node(x, x, null);
        else 
            head = new Node(x, Math.min(x, head.min), head);
    }
    
    public void pop() {
        head = head.next;
    }
    
    public int top() {
        return head.val;
    }
    
    public int getMin() {
        return head.min;
    }
        
    private class Node {
        int val;
        int min;
        Node next;
            
        private Node(int val, int min, Node next) {
            this.val = val;
            this.min = min;
            this.next = next;
        }
    }
}
```

