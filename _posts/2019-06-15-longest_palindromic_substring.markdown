---
layout: post
title:      "Longest Palindromic Substring"
date:       2019-06-15 17:23:22 -0400
permalink:  longest_palindromic_substring
---


#### How to find the longest palindromic substring in a string?


##### First we have to answer the question 'What is a palindrome?"


A palindrome is the same backwards and forwards.


For example, these are all palindromes


  *       "mom"
  *       "racecar"
  *       "taco cat"



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;So when given a string (s) how do we determine if it is a palindrome? First off we need to determine if we will be considering just single words or if we will be considering cases that include spaces. For this situation we will be using single words to make it simpler.




&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Some of the more common solutions include the 'brute force' method or check every substring to see if it is a palindrome. We could also do the expand from the center method which is more efficient than brute force. The best method is to use Manacher's Algorithm which is linear time and I recommend looking it up.



For this blog I am going to explain solving the problem using a matrix.

There are 4 variables to keep track of.
1. Index at where the palindrome starts (start)
2. Length of the palindrome (max)
3. Start index we are considering (i)
4. Index offset (k)
5. The matrix (matrix)




```
def longest_palindrome(s)
  start = 0
	max = 0
	k = 2
	i = 0
	
  matrix = Array.new(s.length) {Array.new(s.length)}

end
```



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;We will iterate through the string and when we run into matching letters (matrix\[i][j]) where matrix\[i+1][j-1] == true we can add another true to the table. To do this we need to initialize the matrix and set all matrix\[i][i] = true because each character is a palindrome of size 1.



```
    while (i < s.length)
        matrix[i][i] = true
        i += 1
    end
```



|   | a | b | b | b | a | b | c |
|---|---|---|:-:|---|---|---|---|
| a | T |   |   |   |   |   |   |
| b |   | T |   |   |   |   |   |
| b |   |   | T |   |   |   |   |
| b |   |   |   | T |   |   |   |
| a |   |   |   |   | T |   |   |
| b |   |   |   |   |   | T |   |
| c |   |   |   |   |   |   | T |



We also need to go through and set matrix\[i][i+1] to true if the characters match else the odd indicies can never be 'true' as you will see when we get to that part of the code.



```
    while (i < s.length - 1)
        if (s[i] == s[i+1])
            matrix[i][i+1] = true
            start = i
            max = 1
        end
         i += 1
    end
```

</br>


|   | a | b | b | b | a | b | c |
|---|---|---|:-:|---|---|---|---|
| a | T |   |   |   |   |   |   |
| b |   | T | T |   |   |   |   |
| b |   |   | T | T |   |   |   |
| b |   |   |   | T |   |   |   |
| a |   |   |   |   | T |   |   |
| b |   |   |   |   |   | T |   |
| c |   |   |   |   |   |   | T |




Now if we go through the rest of the comparisons checking if the chars are the same and the matrix value is true to the bottom left (\[i+1][j-1]) we will end up filling the matrix as such.




|   | a | b | b | b | a | b | c |
|---|---|---|:-:|---|---|---|---|
| a | T |   |   |   | T |   |   |
| b |   | T | T | T |   |   |   |
| b |   |   | T | T |   |   |   |
| b |   |   |   | T |   | T |   |
| a |   |   |   |   | T |   |   |
| b |   |   |   |   |   | T |   |
| c |   |   |   |   |   |   | T |



```
    while (k < s.length)
        while (i < s.length - k)
            j = i + k
            if (s[j] == s[i] && !!matrix[i+1][j-1])
                matrix[i][j] = true

                if (k > max)
                    max = k
                    start = i
                end

            end
            i += 1
        end
        k += 1
        i = 0
    end
```


We start with k = 2 since we already filled in the first two diagonals and then each time we increment k we set i = 0 and in the inner loop j = i + k (offset). At the end we can return the substring using the variables we saved. If we put it all together we have...




```
def longest_palindrome(s)
    start = 0
    max = 0
    i = 0
    k = 2

## always remember to add base cases!
    if (s.length < 3)
        return "" if (s.length < 1)
        return s[0] if (s.length == 1)
        return s[0] == s[1] ? s : s[0]
    end

    matrix = Array.new(s.length) {Array.new(s.length)}

    while (i < s.length)
        matrix[i][i] = true
        i += 1
    end

    i = 0
    while (i < s.length - 1)
        if (s[i] == s[i+1])
            matrix[i][i+1] = true
            start = i
            max = 1
        end
         i += 1
    end

    i = 0
    while (k < s.length)
        while (i < s.length - k)
            j = i + k
            if (s[j] == s[i] && !!matrix[i+1][j-1])
                matrix[i][j] = true

                if (k > max)
                    max = k
                    start = i
                end

            end
            i += 1
        end
        k += 1
        i = 0
    end

    return s[(start_i)..(start_i + max)]
end

```


*And as always don't forget to add your base cases!*


```
    if (s.length < 3)
		
		# empty string as input
        return "" if (s.length < 1)
				
		# string of length 1 should return the char
        return s[0] if (s.length == 1)
				
		# If there are two letters that are the same return the string else just the first char
        return s[0] == s[1] ? s : s[0]
    end
```
