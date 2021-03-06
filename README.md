# Recursion Problems

## Definitions
Define the following:

- Recursion:  In programming, recursion is a method that calls itself within the method. In general, it's defining a problem or solution in terms of itself.
- Recursive Case: Cases when the the input to a method causes the method to call itself.
- Base Case: A case (or cases) in which the input to a method returns a result (without recursion).
- Activation Chain/Stack: The chain of calls to the recursive method that gets added to each time the method calls itself.
- Activation Record/Call: A call to the method that is active but has not yet been returned.
- Infinite Recursion/Stack Overflow/Stack too deep: A recursion that will continue forever.
- Tail Recursion: A recursive method that does some calculations and then passes the result into itself for the next call of the method. The "base case" will then return that calculated result.

## Tracing through a recursive method

### Trace #1
```
def mystery1(n)
  if n == 1
    return n
  else
    return n + mystery1(n-1)
  end
end
```

- What is mystery1(5)? 15
- What is mystery1(10)? 55
- What is mystery1(0)? infinite recursion

### Trace #2
```
def mystery2(n)
  if n < 10
    return n
  else
    return (n%10) + mystery2(n/10)
  end
end
```

- What is mystery2(123)? 6
- What is mystery2(9005)? 14
- What is mystery2(-123)? -123
- _Added Fun: How could we make `mystery2(-123)` work the way we might expect it to work instead of the way it does?_
Probably not the most elegant solution, but I defined a `mystery2_new` in mystery-methods.rb

### Trace #3
```
def mystery3(n)
  if n == 0
    return 100
  elsif n == -1
    return 200
  end
  if n%2 == 0
    return mystery3(n/2)
  else
    return mystery3(n-1)
  end
end
```

- What is mystery3(1)? 100
- What is mystery3(13)? 100
- What is mystery3(-6)? 200

### Trace #4
```
def mystery4(b,e)
  if e == 0
    return 1
  else
    return b * mystery4(b,e-1)
  end
end
```

- What is mystery4(10,2)? 100
- What is mystery4(4,3)? 64
- What is mystery4(5,0)? 1

### Trace #5
```
def mystery5(s)
  if s.length == 0
    return ""
  else
    return "*" + mystery5(s[1..-1])
  end
end
```

- What is mystery5("hi")? "**"
- What is mystery5("")? ""
- What is mystery5("Hi, there!")? "**********"
- _Added Fun: How could we make only alphabetic characters to be changed to stars?_
I defined a `mystery5_new` in mystery-methods.rb.

### Trace #6
```
def mystery6(s)
  if s == nil || s.length == 0
    return ""
  else
    space = 0
    until space >= s.length || s[space] == " "
      space += 1
    end
    return mystery6(s[(space+1)..-1]) + " " + s[0...space]
  end
end
```

- What is mystery6("goodnight moon")? " moon goodnight"
- What is mystery6("Ada Developers Academy")? " Academy Developers Ada"
- What is mystery6("Hi, there!")? " there! Hi,"
- _Added Fun: How could we make the reversal happen by letter, instead of by word (i.e. Make it so that mystery6("goodnight moon") returned "noom thgindoog")?_
I defined a `mystery6_new` in mystery-methods.rb
