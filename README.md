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

### Compare two arrays regardless of order

```
def is_equal(arr1, arr2)
  arr1.sort == arr2.sort
end

is_equal([1,2,3], [2,3,1]) # true
is_equal([1,2,3], [2,3,1,4]) # false
```

### Cloning an array

```
dup_array = [1,2,3].dup

# dup_array = [1,2,3]
```

### Create an array of numbers in the given range

```
a=\*(1..10)
Array (1..10)
(1..10).to_a

# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

("a".."f").to_a

# ["a", "b", "c", "d", "e", "f"]
```

### Create cartesian product

```
[:a, :b].product [:c,:d]

# [[:a, :c], [:a, :d], [:b, :c], [:b, :d]]
```

### Empty an array

```
a.clear
```

### Find the closest number from an array

```
def find_closest(n, arr)
  arr.min_by{|x| (n-x).abs}
end

arr = [20, 30, 45, 50, 56, 60, 64, 80]
find_closest(40, arr) # 45
```

### Find the index of the maximum item of an array

```
arr.index(arr.max)

arr = [20, 30, 45, 50, 56, 60, 64, 80]
arr.index(arr.max) # 7
```

### Find the index of the minimum item of an array

```
arr.index(arr.min)

arr = [20, 30, 45, 50, 56, 60, 64, 80]
arr.index(arr.max) # 0
```

### Find the length of the longest string in an array

```
def find_longest_length(arr)
  arr.max_by(&:length)
end

arr = ['one','two','three','four','five']
find_longest_length(arr) # "three"
```

### Create an array of cumulative sum

```
def cumulative_sum(arr)
  sum = 0
  arr.map{|x| sum += x}
end

arr = [1, 2, 3, 4]
cumulative_sum(arr) # [1, 3, 6, 10]
```

### Flatten an array

```
c = [[["a"]], [["b"]]]
c.flatten # ["a", "b"]

c.flatten(1) # [["a"], ["b"]]
```

### Get all arrays of consecutive elements

```
def get_consecutives_arrays(arr, n)
  arr.each_cons(n).to_a
end

arr = [1, 2, 3, 4]
get_consecutives_arrays(arr, 2) # [[1, 2], [2, 3], [3, 4]]
get_consecutives_arrays(arr, 3) # [[1, 2, 3], [2, 3, 4]]
```

### Get the average of an array

```
def array_average(arr)
  arr.sum(0.0) / arr.size
end

arr = [1, 2, 3, 4, 5, 6, 7, 8]
array_average(arr) # 4.5
```

### Intersection, union & difference

```
x = [1, 1, 2, 4]
y = [1, 2, 2, 2]

# intersection
x & y # [1, 2]

# union
x | y # [1, 2, 4]

# difference
x - y # [4]
```

### Get the rank of an array of numbers

```
def numbers_rank(arr)
  rank = 1
  arr.each_with_index.map{|value, i| arr[i-1] == value ? rank : rank = i+1}
end

arr = [89, 52, 52, 36, 18, 18, 5]
numbers_rank(arr) # [1, 2, 2, 4, 5, 5, 7]
```

### Remove duplicate values in an array

```
arr.uniq

arr = [1,1,1,2,3,4,5]
arr.uniq # [1, 2, 3, 4, 5]
arr # [1,1,1,2,3,4,5]
```

### Intersperse element between elements

```
def intersperse_element(arr, element)
  arr.flat_map { |x| [x, element] }[0...-1]
end

arr = [1, 2, 3]
intersperse_element(arr, :a) #  [1, :a, 2, :a, 3]
```

### Partition an array based on a condition

```
arr.partition { condition }

(1..6).partition { |v| v.even? } # [[2, 4, 6], [1, 3, 5]]
```

### Remove nil / false values from array

```
arr - [ nil ] # removes nil values
array.compact #removes nil values

arr - [ false ] # removes false

arr - [ nil, false ] #removes nil and false
arr.select(&:itself) # removes nil and false


arr = [0, "a string", "", true, 5, "another string", false, nil]
arr - [ nil ] # [0, "a string", "", true, 5, "another string", false]
arr - [ false ] # [0, "a string", "", true, 5, "another string", nil]
arr - [ nil, false ] # [0, "a string", "", true, 5, "another string"]
```

### Sort an array of items by given key

```
def sort_array_by(arr, key)
  arr.sort_by{ |hash| -(hash[key] || 0) }.reverse
end

arr = [
  { name: 'Foo', age: 42 },
  { name: 'Bar', age: 24 },
  { name: 'Fuzz', age: 36 },
  { name: 'Baz', age: 32 },
];

sort_array_by(arr, 'age')
# [{:name=>"Baz", :age=>32}, {:name=>"Fuzz", :age=>36}, {:name=>"Bar", :age=>24}, {:name=>"Foo", :age=>42}]
```

### Shuffle an array

```
arr.shuffle

arr1 = [1, 2, 3, 4, 5]
arr2 = ["a", "b", "c", "d", "e"]

arr1.shuffle # ["a", "b", "c", "d", "e"]
arr2.shuffle # ["e", "a", "b", "c", "d"]
```

### Swap the rows and columns of a matrix

```
matrix.transpose


matrix = [
  [1,2,3],
  [1,2,3],
  [1,2,3]
]
matrix.transpose # [[1, 1, 1], [2, 2, 2], [3, 3, 3]]
```

### Swap two array items

```
def swap_items(arr, key1, key2)
 arr[key1], arr[key2] = arr[key2], arr[key1]
end

arr = [4, 5, 6, 7]
swap_items(arr, 1 ,2)
arr # [4, 6, 5, 7]
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
