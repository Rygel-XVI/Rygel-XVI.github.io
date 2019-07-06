---
layout: post
title:      "Container with the Most Water - Code Challenge"
date:       2019-07-06 21:29:15 +0000
permalink:  container_with_the_most_water_-_code_challenge
---


[Leetcode Problem 11](https://leetcode.com/problems/container-with-most-water/)



This problem is pretty straight forward.

Given an array of heights, find the two indices that could contain the most water between them.


Generally there are two ways of solving this, the brute force method, and the two pointer method.


### Brute Force

This method will calculate every possible combination possible to determine the answer. This requires a nested loop resulting in a complexity of O(n^2).


Javascript
```

var maxArea = function(height) {
    let mostWater = 0
    
    for (let l = 0; l < height.length - 1; l++) {
        for (let r = height.length - 1; r > l; r--) {
            mostWater = Math.max(mostWater, (Math.min(height[l], height[r])*(r-l)))
        }        
    }
    return mostWater
}
```

A better way of doing this is to utilize two pointers.


### Two Pointer Method

For this method we utilize two pointers that are placed on opposite ends of the array to iterate through once resulting in a time complexity of O(n). The area between the current left (l) and right (r) indexes and if the area is larger than the current max, it is set as max.

The indices are moved based on which one is smaller or if equal the left one in this situation. It is arbitrary which is checked in the if statement.

Javascript
```
var maxArea = function(height) {
    let max = 0
    
    let l = 0
    let r = height.length - 1
    
    while (l < r) {
        if (height[l] > height[r]) {
            mostWater = Math.max(height[r] * (r-l), max)
            r--
        } else {
            mostWater = Math.max(height[l] * (r-l), max)
            l++ 
        }       
    }
    
    return max
};
```

In Ruby...
```
def max_area(height)
    max_area = 0
    
    l_idx = 0
    r_idx = height.length - 1
    
    while (r_idx > l_idx)  
        if height[r_idx] >= height[l_idx]
            max_area = [(height[l_idx] * (r_idx - l_idx)), max_area].max
            l_idx += 1
        else 
            max_area = [(height[r_idx] * (r_idx - l_idx)), max_area].max
            r_idx -= 1
        end        
    end
    
    return max_area
end
```








