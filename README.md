# alse-s-schema
A personal attempt for a less powerful but more easy to use json schema
# idea
more about number and enum, for mock.
# number
- a sold number is ok
- use a string startsWith "n-" or "i-" or "f-"
    n means number, both integer and float
    i, f, as you can guess
  then some pattern:
    min~max
    :N the multiple of the N
  `i-3~77:5` fits integer gt 3 and lt 77 and multiples 5:5,10,15,20,25,30,35,...,75
# null, undefined
  just type it in.
# string
  less powerful
  if a string starts with "x-", use backslash to escape it
# array
  use "[]" to express it.
  the start can be object {"$header":...}, this is the config
  the end can be object {"$rest":...},this defines how to treat tails
# object
  key and value are of use.
  key startsWith "+" means required
  key startsWith "*" means optional
  key startsWith "!" means should not appear
  key startsWith "-" means branch.It contains something
    the main key without "-" is the branchname, and the inner value should be a object.
    the key in inner object means the value range of the source;
      like {"-enum":{a:23,b:"abcd"}} can fits {"-enum":"a",a:23} and {"-enum":"a",b:"abcd"}
      inner are suits for outer.
      and {"-ip":{v4:["n-1~255"],v6:["n-1~65535"]},"-header":{content:"text|image|video"}}
      I should define more on key-value
    
  and key "$config" configs more information
    like size, rest, or so
  
  
