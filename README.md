# Ruby / Rails - one liners

Show off your favorite line method / function in ruby / rails.

Leave a ⭐️ if you find this helpful.

# Content

## ARRAYS / HASHES

#### From array to hash

```
def make_me_a_hash(arr)
  Hash[(0...arr.size).zip arr]
end

arr = ["one", "two", "three", "four", "five"]
make_me_a_hash(arr) # {0=>"one", 1=>"two", 2=>"three", 3=>"four", 4=>"five"}
```

#### Remove duplicate elements

```
def remove_duplicate(arr)
  arr.uniq
end

remove_duplicate([1,1,2]) # [1,2]
```

#### Most appeared element

```
def get_most_appeared(arr)
 arr.max_by {|i| arr.count(i)}
end

pets = [ 'dog', 'dog', 'cat', 'bird', 'chinchilla', 'rat', 'hamster', 'dog', 'rat', 'bird', 'cat', 'giraffe', 'cat', 'bird','dog', 'snake', 'hamster', 'dog' , 'mouse', 'spider', 'dog', 'cat']
get_most_appeared(pets) # 'dog'
```

## FUNCTIONS

#### Inline if-else

```
<condition> ? "true" : "false"
```

## STRINGS

#### Reverse string

```
"string".reverse #gnirts
```

#### Palindrome?

```
def is_palindrome?(str)
  str == str.reverse
end

is_palindrome?('hello') # false
is_palindrome?('worldlrow') # true
is_palindrome?('12321') # true
```

#### Repeat 'n' times

```
def repeat(text, n=1)
  text * n
end

def repeat_with_spaces(text, n=1)
  ("#{input} " * n).strip
end
​
repeat('hello', 3) # hellohellohello
repeat_with_spaces('hello', 3) # hello hello hello
```

#### Capitalize ONLY first letter

```
"hello world".capitalize
# "Hello world"
```

#### Capitalize first letter of each word

```
"hello world".titleize # RAILS
"hello_world".titleize # RAILS
# "Hello World"

"hello world".split(/ |\_|\-/).map(&:capitalize).join(" ") # RUBY
```

## VARIABLES

#### Assign multiple variables in single line

```
a, b, c = 'a', 123, [1,2,3,4,5]

a # 'a'
b # 123
c # [1,2,3,4,5]
```

#### SWAPPING

```
a, b = b, a

a = 5
b = 10
a # 10
b # 5
```

## RANDOM

#### Generate random boolean

```
[true, false].sample
```

#### Generate random integer in given range

```
def generate_random(min, max)
  rand(min..max)
end

generate_random(1,10) # 3
generate_random(-5,10) # -3
generate_random(100,1) # nil
```

#### Generate random hex color

```
def generate_hex
"%06x" % (rand * 0xffffff)
end


generate_hex # 285b36
generate_hex # cf4eed
```

# Contributing♦️

Submit your PR with your favorite line of code.

Please, add the code snippet to the corresponding category.

Don't forget to always show an example of how your one-liner code works!

<i>Inspired by: https://github.com/phuocng/1loc</i>
