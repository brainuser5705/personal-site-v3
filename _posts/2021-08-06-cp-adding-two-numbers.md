---
title: "cp: Adding Two Numbers"
layout: post
categories: cp progamming
---

*[Leetcode]()*

## My Inital Solution
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        
        ListNode currentNode = null;
        ListNode newNode = null;
        
        // the first node of the solution
        // this is the node to return
        ListNode firstNode = null;
        boolean firstPass = true;
        
        int d1, d2;
        boolean overTen = false;
        
        // You keep adding new nodes if there are still nodes to go through and if you need to add an extra one because of carry over
        while (l1 != null || l2 != null || overTen /* (7) */){
            
            /* (4) (5) */
            // Creates a new current node
            newNode = new ListNode();
            if (currentNode != null){
                // If there was a previous current node, then its next value should this new current node
                currentNode.next = newNode;
            }
            currentNode = newNode;
            
            // After the first loop, the first node should not be reassigned
            if (firstPass){
                firstNode = currentNode;
                firstPass = false;
            }
            
            /* (1) */
            // Gets the digit of the nodes if possible
            if (l1 == null){
                d1 = 0;
            }else{
                d1 = l1.val;
            }

            if (l2 == null){
                d2 = 0;
            }else{
                d2 = l2.val;
            }
            
            /* (2) */
            // Get the sum of the two notes
            int sum = d1 + d2;
            if (overTen){ 
                // add one if carry over from previous node
                sum += 1;
            }
            
            // The digit to put into the node must be single-digit
            int digit;
            if (sum >= 10){
                // Set overTen to true if there is a carry over
                digit = sum % 10;
                overTen = true;
            }else{
                digit = sum;
                overTen = false;
            }
            currentNode.val = digit;
            
            // Move on to the next node
            try{
                l1 = l1.next;
            }catch (NullPointerException e){
                l1 = null;
            }
            try{
                l2 = l2.next;
            }catch (NullPointerException e){
                l2 = null;
            }
    
        }
        
        return firstNode;
        
    }
}
```

---

## LeetCode Solution
*modified variables names and ordering to be similar to my code*
```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        
        /* (3) */
        ListNode firstNode = new ListNode();
        
        int d1, d2;
	    int overTen;
        ListNode currentNode = firstNode;
        while (l1 != null || l2 != null){
            
            /* (1) */
            int d1 = (l1 == null) ? 0 : l1.val;
	        int d2 = (l2 == null) ? 0 : l2.val;
            
            /* (2) */
            int sum = overTen + d1 + d2;
	        overTen = sum / 10;
   
            /* (4) */
	        currentNode.next = new ListNode(sum % 10)
            currentNode = currentNode.next;
            
            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
    
        }

        /* (7) */
        if (overTen > 0) {
            currentNode.next = new ListNode(overTen);
        }
        
        return firstNode.next;
        
    }
}
```

Overall the approach is the same: go through the list, get the digit and make the new node. However, Leetcode simplify most of the operations. Here are the differences:

### Getting the Digit
1. Setting the value with a ternary operator instead of an if statement.
2. Using integer division and modulus operator to get carry out digit and digit to put into node. (Also storing the carry digit in an int rather than using a boolean)

### Returning the first Node
3. Using a dummy node to keep track of the first node, then return the first node by returning its `next` node (`firstNode.next`).

### Creating a New Node

4. Instead of using another variable to create the next node, you can directly assign the next node to `currentNode.next` and pass the digit as the `val` argument. Then increment `currentNode` by assigning it to its `next` node. 

5. **In fact, you are getting the digit for the next node**. With this you are creating the new node after getting the digit. For example, because of the dummy node, you do not need to check if `currentNode` is null for the first loop to make the next node. You can also create the next node after getting the digit.

### Moving on to next node
6. Check the current node, then assign instead of checking the next node then assign.

### Extra carry digit
7. Create the new carry digit with the same process: make the new node with a constructor and assign it `currentNode.next` (4). In my code, if the boolean `overTen` was still true, it would make another node.

---

## Major Takeaways
1. Use a dummy node to keep track of first node.
2. In the same concept, get the value for the next node and then assign the new node using its constructor rather than making the current node first then assigning its value.
