---
layout: post
title:      "Reverse Integer - Code Challenge"
date:       2019-06-30 23:01:11 +0000
permalink:  reverse_integer_-_code_challenge
---


Leetcode Problem 7

### Given a 32-bit signed integer, reverse digits of an integer.

Examples:
Input: -123
Output: -321

Input: 120
Output: 21

Input: 123
Output: 321



At first glance this problem is easy. In Ruby just convert to string, reverse, and convert back to integer and Ruby has all those nice built in functions to do just that and make it easy.

```
def reverse(x)
    
    x.to_s.reverse.to_i

end
```


However, this will not accomodate a negative number as the reverse function does not accomodate then negative. So this is what happens.

```
irb(main):016:0> x = -123
=> -123
irb(main):017:0> x.to_s.reverse.to_i
=> 321

```

where what we really want is -321 and one way to accomodate this is to create a variable that indicates whether or not it should be negative and add it if necessary on the return statement.

```
def reverse(x)
    
		neg = x < 0
		
    x.to_s.reverse.to_i
		
		return neg ? -x : x

end

```

Almost there. We have not considered a key part of the problem. It is a 32-bit integer.

Integers can be huge, however, when programming there are limitations. Technically you could have a number that is infinite -1 places long and have it be an integer but that would also break whatever you are working on. So when the question asks 32-bit integer what we are saying is largest binary number with 32 places so...



11111111111111111111111111111111    which ends up as 4294967295 in base 10 math.



However, the problem also specifies signed so the first bit is a + or - resulting in 31 1's not 32 so we end up with 


2147483648


so the range is -2147483648 to 2147483648 right? But what about 0? Well the positive integer takes it so the range ends up being


-2147483648 to 2147483647 non-inclusive of those numbers.


So to accomodate this we have to check if the integer input is greater or less than those ranges before returning a result. We end up with this.

```
def reverse(x)
    
    neg = x < 0
    x = x.to_s.reverse.to_i
        
    return  0 if (x > 2147483646 || x < -2147483647)
    
    return neg ? -x : x
end
```

If you wanted to not use as many built in functions building out the reverse is always good practice.

```
def reverse(x)
    i = 0
    
    neg = x < 0
    x = x.to_s
    
    x.length % 2 == 0? (half = x.length/2) : (half = x.length/2 + 1)
    len = x.length - 1
    
    while i < half
      temp = x[i]        
      x[i] = x[len - i]
      x[len - i] = temp
      i += 1
    end
    
    x = x.to_i
    
    return  0 if (x > 2147483646 || x < -2147483647)
    
    return neg ? -x : x
end
```


In Javascript we end up with


```
var reverse = function(x) {
    const neg = x < 0
    
    x = Math.abs(x).toString().split("").reverse().join("")
    x = parseInt(x)
  
    if (neg) {
        x = - + x
    }
    
    if (x < -2147483647 || x > 2147483646){
        return 0
    } else {
        return x
    }
}
```

Of course the parseInt can be combined with the line above it but it's a little easier to read on a different line.

Until my next code challenge.


