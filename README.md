# Recursion Problems

## Definitions
Define the following: 

- Recursion
- Recursive Case
- Base Case
- Activation Chain/Stack
- Activation Record/Call
- Infinite Recursion/Stack Overflow/Stack too deep
- Tail Recursion

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

- What is mystery1(5)? 
# Answer: 5 + 4 + 3 + 2 + 1 = 15
- What is mystery1(10)?
# Answer: 10 + 9 + 8 + 7 + 6 +5 + 4 + 3 + 2 + 1 = 55
- What is mystery1(0)?
# Answer: infinite recursion (never hits base case n == 1)

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

- What is mystery2(123)?
# Answer: 3 + 2 + 1 = 6
- What is mystery2(9005)?
# Answer: 5 + 0 + 0 + 9 = 14
- What is mystery2(-123)?
# Answer: -123
- _Added Fun: How could we make `mystery2(-123)` work the way we might expect it to work instead of the way it does?_
# Answer: Add a conditional so that if the argument is negative, multiply it by -1

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

- What is mystery3(1)?
# Answer: m3(1) -> m3(0) = 100
- What is mystery3(13)? 
# Answer: 100
- What is mystery3(-6)?
# Answer: 200

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

- What is mystery4(10,2)?
# Answer: 10 * 10 * 1 = 100
- What is mystery4(4,3)?
# Answer: 4 * 4 * 4 * 1 = 64
- What is mystery4(5,0)?
# Answer: 1

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

- What is mystery5("hi")?
# Answer: "**"
- What is mystery5("")?
# Answer: ""
- What is mystery5("Hi, there!")?
# Answer: "**********"
- _Added Fun: How could we make only alphabetic characters to be changed to stars?_
 

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

- What is mystery6("goodnight moon")?
# Answer: " moon goodnight"
- What is mystery6("Ada Developers Academy")?
# Answer: " Academy Developers Academy"
- What is mystery6("Hi, there!")?
# Answer: " there! Hi,"
- _Added Fun: How could we make the reversal happen by letter, instead of by word (i.e. Make it so that mystery6("goodnight moon") returned "noom thgindoog")?_
