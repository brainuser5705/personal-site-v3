*[Leetcode](https://leetcode.com/problems/longest-substring-without-repeating-characters/)*

## My Solution
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        int solution = 0;
        String temp = "";
        
        int index = 0;
        // Last index keeps track of the latest index in the string to start from
        int lastIndex = 0;

        while (index < s.length()){
            
            char c = s.charAt(index);
            
            // Checks to see if the character is in the string
            if (temp.indexOf(c) < 0){
                temp += Character.toString(c);
                index++; // continue adding characters to the stack
            }else{
                // reset the temporary stack and for the next loop, start in the next index
                temp = "";
                lastIndex++;
                index = lastIndex;
            }
            
            // If the temporary stack is longer, that is the new solution.
            if (temp.length() > solution){
                solution = temp.length();
            }
            
        }
        
        return solution;
        
    }
}
```

The two main parts of my solution is the temporary string `temp`, which I use as a stack of characters, and an index variable `lastIndex` which increments from each character of `s`.  
Essentially, it starts from each character of `s` using `lastIndex` as its tracker. It will then use `index` to go along the string and add the characters to `temp` if it is not already there. If the character already exists in `temp`, then `temp` will reset and `lastIndex` will move on to the next character to start from. At the end of loop, it checks to see if `temp` is the new solution and if so, it will put its length in `solution`.  
 
**Notes**  
1. You need to put the checking of the solution outside of the if-else statement, not only when you reset it, because the loop can stop after one character and never replace `solution`. For instance, the case `" "`.
2. Although there is only one while loop, the time complexity is actually `O(n^2)`. To make clear again, `index` is used for incrementing along the string for each starting character, where as `lastIndex` is used for tracking that starting character. So when `temp` is reset because of a duplicate character, `lastIndex` will increment to the next character to start from and `index` will reset to `lastIndex` again be used to increment along the string. That means you are going back and forth in the string for each character of the string, making the time complexity `O(n^2)`.

---

## [Redquark](https://redquark.org/leetcode/0003-longest-substring-without-repeating-characters/) Solution
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        int start = 0, end = 0, maxLength = 0;
        Set<Character> uniqueCharacters = new HashSet<>();

        // base case
        if (s == null || s == ""){
            return 0;
        }

        while(end < s.length()){

            if (uniqueCharacters.add(s.charAt(end))){
                end++;
                maxLength = Math.max(maxLength, uniqueCharacters.size());
            }else{
                start++;
                uniqueCharacters.remove(s.charAt(start));
            }
        }

        return maxLength;
        
    }
}
```
This solution uses the *Sliding Window Algorithm*.

**Key points and differences from my approach**
1. Instead of using `s.indexOf()`, this approach uses a Set to store the unique characters, reducing lookup time. 
2. It stores the `maxLength` integer **only** and does not keep track of the substring.
3. By using a start and end pointer, it does not need to start from all the characters in the string. The search will stop when the end pointer reaches the end of the string. This reduces the time complexity to O(n).
4. Because the final substring has to be contiguous, the string will remove the character at the start pointer. This is similar to my approach where you increment `lastIndex` to move on to the next character to start from. Note that even if the character is part of the final substring, its length will already be stored in `maxLength`. This gets rid of the need to check the length of the string every loop.
5. It uses `Math.max()` to get the maximum length with the set `uniqueCharacters`'s size, instead of needing to check the length of the substring.

---

## More about the *Sliding Window Algorithm*

Redquark wrote a great [article](https://redquark.org/cotd/sliding_window/) explaining how the algorithm works. Here are my notes:

The algorithm deals with linear data structures (lists, arrays, strings) where the goal is to find some longest/shortest property.  

The idea is that you can "slide" along the data structure with an optional *window size*. For example, these would be the test cases if the window size is 2 and the array is `[a, b, c, d, e, f]`.
```
[a,b]
  [b,c]
    [c,d]
      [d,e]
        [e,f]
```
Notice that for each slide (or more programatically, each loop), the left element is discarded.

---

## Major Takeaways
1. Use a set when storing unique elements to reduce lookup time.
2. Use a start and end pointer (part of the Sliding Window algorithm) when searching for *contiguous* solutions to avoid needing to test every single element.
3. Store only what is necessary (in this case, the length not the substring) which reduces the need to check for a value at the end of every loop.


