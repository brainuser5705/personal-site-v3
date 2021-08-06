---
layout: post
title: "cp: Two Sums"
categories: cp programming
---

*[Leetcode](https://leetcode.com/problems/two-sum/)*

## Brute Force
Loop through each number (element) pair until their sums equals target.
```java
for (int i = 0; i < nums.length-1 /*(1)*/; i++){
    for (int j = i+1 /*(2)*/ ; j < nums.length; j++){
        if (nums[i] + nums[j] == target){
            return new int{i, j};
        }
    }
}
return null;
```
**Notes**  
1. Because you are pairing, it does not make sense for the first number of the pair (tracked by index `i`) to be the last element in `nums` otherwise there would be no more elements to pair with.
2. You start the search of the second number (tracked by `j`) after the first nummber because all the numbers before the first number were already paired in previous loops. You also do not start at the first number because you cannot use the same element.

---

## Hash Table
For each element in the array, see if its complement (target - value of element) exists then map its value to its index.  
```java
Map<Integer, Integer> map = new Hashmap<>();
for (int i = 0; i < nums.length; i++){
    
    // check complement
    int complement = target - nums[i];
    if (map.containsKey(complement) && map.get(complement) != i /*(1)*/){
        return new int{i, map.get(complement)};
    }

    // put in map
    map.put(nums[i], i);

}
return null;
```
**Notes**
1. The complement's index should not be the same as the current element (`i`). [More notes]

By putting the numbers and indexes in a hashmap, it reduces lookup time to O(1). You also do not need to pair every number, instead you can finds its complement.

1. What if there are duplicate numbers in `nums` like in `nums=[0,4,3,0], target=0`?  
You are checking the complement first, meaning that the `map` will contain the latest index and not map the new index just yet.  Then you would return the `{index in map, index of for loop}`

2. Is the time complexity always O(1)?  
If there is a collision, the time complexity is O(n) however amortized time is O(1).


