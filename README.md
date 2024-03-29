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

#### Compare two arrays regardless of order

```
def is_equal(arr1, arr2)
  arr1.sort == arr2.sort
end

is_equal([1,2,3], [2,3,1]) # true
is_equal([1,2,3], [2,3,1,4]) # false
```

#### Cloning an array

```
dup_array = [1,2,3].dup

# dup_array = [1,2,3]
```

#### Create an array of numbers in the given range

```
a=\*(1..10)
Array (1..10)
(1..10).to_a

# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

("a".."f").to_a

# ["a", "b", "c", "d", "e", "f"]
```

#### Create cartesian product

```
[:a, :b].product [:c,:d]

# [[:a, :c], [:a, :d], [:b, :c], [:b, :d]]
```

#### Empty an array

```
a.clear
```

#### Find the closest number from an array

```
def find_closest(n, arr)
  arr.min_by{|x| (n-x).abs}
end

arr = [20, 30, 45, 50, 56, 60, 64, 80]
find_closest(40, arr) # 45
```

#### Find the index of the maximum item of an array

```
arr.index(arr.max)

arr = [20, 30, 45, 50, 56, 60, 64, 80]
arr.index(arr.max) # 7
```

#### Find the index of the minimum item of an array

```
arr.index(arr.min)

arr = [20, 30, 45, 50, 56, 60, 64, 80]
arr.index(arr.max) # 0
```

#### Find the length of the longest string in an array

```
def find_longest_length(arr)
  arr.max_by(&:length)
end

arr = ['one','two','three','four','five']
find_longest_length(arr) # "three"
```

#### Create an array of cumulative sum

```
def cumulative_sum(arr)
  sum = 0
  arr.map{|x| sum += x}
end

arr = [1, 2, 3, 4]
cumulative_sum(arr) # [1, 3, 6, 10]
```

#### Flatten an array

```
c = [[["a"]], [["b"]]]
c.flatten # ["a", "b"]

c.flatten(1) # [["a"], ["b"]]
```

#### Get all arrays of consecutive elements

```
def get_consecutives_arrays(arr, n)
  arr.each_cons(n).to_a
end

arr = [1, 2, 3, 4]
get_consecutives_arrays(arr, 2) # [[1, 2], [2, 3], [3, 4]]
get_consecutives_arrays(arr, 3) # [[1, 2, 3], [2, 3, 4]]
```

#### Get the average of an array

```
def array_average(arr)
  arr.sum(0.0) / arr.size
end

arr = [1, 2, 3, 4, 5, 6, 7, 8]
array_average(arr) # 4.5
```

#### Intersection, union & difference

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

#### Get the rank of an array of numbers

```
def numbers_rank(arr)
  rank = 1
  arr.each_with_index.map{|value, i| arr[i-1] == value ? rank : rank = i+1}
end

arr = [89, 52, 52, 36, 18, 18, 5]
numbers_rank(arr) # [1, 2, 2, 4, 5, 5, 7]
```

#### Remove duplicate values in an array

```
arr.uniq

arr = [1,1,1,2,3,4,5]
arr.uniq # [1, 2, 3, 4, 5]
arr # [1,1,1,2,3,4,5]
```

#### Intersperse element between elements

```
def intersperse_element(arr, element)
  arr.flat_map { |x| [x, element] }[0...-1]
end

arr = [1, 2, 3]
intersperse_element(arr, :a) #  [1, :a, 2, :a, 3]
```

#### Partition an array based on a condition

```
arr.partition { condition }

(1..6).partition { |v| v.even? } # [[2, 4, 6], [1, 3, 5]]
```

#### Remove nil / false values from array

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

#### Sort an array of items by given key

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

#### Shuffle an array

```
arr.shuffle

arr1 = [1, 2, 3, 4, 5]
arr2 = ["a", "b", "c", "d", "e"]

arr1.shuffle # ["a", "b", "c", "d", "e"]
arr2.shuffle # ["e", "a", "b", "c", "d"]
```

#### Swap the rows and columns of a matrix

```
matrix.transpose


matrix = [
  [1,2,3],
  [1,2,3],
  [1,2,3]
]
matrix.transpose # [[1, 1, 1], [2, 2, 2], [3, 3, 3]]
```

#### Swap two array items

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

## MATHS

#### Calculate the midpoint between two points

```
def midpoint(point1, point2)
  [(point1[0] + point2[0]) / 2, (point1[1] + point2[1]) / 2]
end

midpoint([0, 0], [1, 1]) # [0.5, 0.5]
midpoint([0, 0], [2, 4]) # [1, 2]
```

#### Calculate the linear interpolation between two numbers

```
def linear_interpolation(y1, y2, mu)
  y1 * (1 - mu) + y2 * mu
end

linear_interpolation(0, 1, 0.5) # 0.5
linear_interpolation(0, 1, 0.25) # 0.25
```

#### Check if a point is inside a rectangle

```
def is_point_in_rectangle(point, rectangle)
  point[0] >= rectangle[0] && point[0] <= rectangle[2] && point[1] >= rectangle[1] && point[1] <= rectangle[3]
end

is_point_in_rectangle([1, 1], [0, 0, 2, 3]) # true
is_point_in_rectangle([1, 1], [0, 0, 0.5, 0.5]) # false
```

#### Calculate the angle of a line defined by two points

```
def angle(point1, point2)
  Math.atan2(point2[1] - point1[1], point2[0] - point1[0]) * 180 / Math::PI
end

angle([0, 0], [1, 1]) # 45
angle([0, 0], [1, 0]) # 0
```

#### Check if a rectangle contains other one

```
def is_rectangle_contained(rectangle1, rectangle2)
  rectangle1[0] <= rectangle2[0] && rectangle1[1] <= rectangle2[1] && rectangle1[2] >= rectangle2[2] && rectangle1[3] >= rectangle2[3]
end

is_rectangle_contained([0, 0, 2, 2], [1, 1, 1.5, 1.5]) # true
is_rectangle_contained([0, 0, 2, 2], [1, 1, 3, 3]) # false
```

#### Calculate the distance between two points

```
def distance(point1, point2)
  Math.hypot(point2[0] - point1[0], point2[1] - point1[1])
end

distance([0, 0], [1, 1]) # 1.4142135623730951
distance([0, 0], [5, 0]) # 5
```

#### Convert degrees to radians

```
def degrees_to_radians(degrees)
  degrees * Math::PI / 180
end

degrees_to_radians(180) # 3.141592653589793
degrees_to_radians(90) # 1.5707963267948966
```

#### Check if a rectangle overlaps other one

```
def is_rectangle_overlapping(rectangle1, rectangle2)
  rectangle1[0] < rectangle2[2] && rectangle1[2] > rectangle2[0] && rectangle1[1] < rectangle2[3] && rectangle1[3] > rectangle2[1]
end

is_rectangle_overlapping([0, 0, 2, 2], [1, 1, 3, 3]) # true
is_rectangle_overlapping([0, 0, 1, 1], [2, 2, 3, 3]) # false
```

#### Normalize the ratio of a number in a range

```
def normalize_ratio(num, min, max)
  (num - min) / (max - min)
end

normalize_ratio(0.5, 0, 1) # 0.5
normalize_ratio(5, 0, 10) # 0.5
```

#### Convert radians to degrees

```
def radians_to_degrees(radians)
  radians * 180 / Math::PI
end

radians_to_degrees(3.141592653589793) # 180
radians_to_degrees(1.5707963267948966) # 90
```

#### Round a number to the nearest multiple of a given value

```
def round_to_multiple(num, multiple)
  (num / multiple).round * multiple
end

round_to_multiple(13, 5) # 15
round_to_multiple(12, 5) # 10
```

## NUMBERS

#### Calculate Fibonacci numbers

```
fibo = Hash.new{ |h,k| h[k] = k < 2 ? k : h[k-1] + h[k-2] }

fibo[1] # 1
fibo[2] # 1
fibo[3] # 2
fibo[4] # 3
fibo[5] # 5
fibo[6] # 8
```

#### Add an ordinal suffix to a number

```
def add_ordinal(num)
  num.to_s + %w{th st nd rd th th th th th th}[num % 10]
end

add_ordinal(2) # '2nd'
add_ordinal(11) # '11tst'

```

#### Calculate the average of arguments

```
def average(*args)
  args.reduce(:+) / args.length.to_f
end

average(1, 2, 3, 4) # 2.5
```

#### Calculate the division of arguments

```
def division(*args)
  args.reduce(:/).to_f
end

division(1, 2, 3, 4) # 0.0
```

#### Calculate the mod of collection index

```
def mod(a, b)
  ((a % b) + b) % b
end

mod(-1, 5) # 4
mod(3, 5) # 3
mod(6, 5) # 1
```

#### Calculate the remainder of division of arguments

```
def remainder(*args)
  args.reduce(:%)
end

remainder(1, 2, 3, 4) # 1
```

#### Clamp a number between two values

```
def clamp(val, min = 0, max = 1)
  [min, [val, max].min].max
end

clamp(199, 10, 25) # 25
```

#### Compute the greatest common divisor between two numbers

```
def gcd(a, b)
  b == 0 ? a : gcd(b, a % b)
end

gcd(10, 15) # 5
```

#### Calculate the factorial of a number

```
def factorial(n)
  n <= 1 ? 1 : n * factorial(n - 1)
end

factorial(2) # 2
factorial(3) # 6
factorial(4) # 24
factorial(5) # 120
factorial(6) # 720
```

#### Calculate the sum of arguments

```
def sum(*args)
  args.reduce(:+)
end

sum(1, 2, 3, 4) # 10
```

#### Convert a number to equivalent characters

```
str.chr

99.chr # "c"
```

#### Convert a string to equivalent number

```
"2".to_i # 2
```

#### Convert decimal to binary recursively

```
def decimal_to_binary(num)
  num == 0 ? "" : decimal_to_binary(num/2) + num.divmod(2)[1].to_s
end

decimal_to_binary(10) # 1010
```

#### Get the arrays of digits from a number

```
def digit_array(num)
  num.to_s.chars.map(&:to_i)
end

digit_array(123) # [1,2,3]

```

#### Prefix an integer with zeros

```
def prefix_with_zeros(num, size)
  num.to_s.rjust(size, '0')
end

prefix_with_zeros(42, 5) # 00042

```

#### Multiply arguments

```
def multiply(*args)
  args.reduce(:*)
end

 multiply(1,  2, 3, 4) # 24

```

#### Round a number to a given number of digits

```
def round_to_digits(num, digits)
  num.round(digits)
end

round_to_digits(1.234567, 3) # 1.235

```

#### Subtract arguments

```
def subtract(*args)
  args.reduce(:-)
end

subtract(1, 2, 3, 4) # -8

```

#### Truncate a number at decimal

```
def truncate_at_decimal(num)
  num.to_i
end

truncate_at_decimal(25.198726354) # 25
```

#### Truncate a number to a given number of decimal places without rounding

```
def truncate_without_rounding(num, digits)
  num.truncate(digits)
end

truncate_without_rounding(25.198726354, 1) # 25.1
```

## FUNCTIONS

#### Inline if-else

```
<condition> ? "true" : "false"
```

## STRINGS

#### Capitalize a string

```
def capitalize(string)
  string.capitalize
end

capitalize('fooBar') # 'FooBar'
```

#### Check if a path is relative

```
def is_relative_path(path)
  !path.start_with?('/')
end

is_relative_path('foo/bar') # true
is_relative_path('/foo/bar') # false

```

#### Check if a string is a palindrome

```
def is_palindrome(string)
  string == string.reverse
end

is_palindrome('tacocat') # true
is_palindrome('awesome') # false

```

#### Check if a URL is absolute

```
def is_absolute_url(url)
  url.start_with?('http://', 'https://')
end

is_absolute_url('https://google.com') # true
is_absolute_url('google.com') # false
```

#### Check if two strings are anagram

```
def is_anagram(string1, string2)
  string1.downcase.chars.sort == string2.downcase.chars.sort
end

is_anagram('iceman', 'cinema') # true
is_anagram('foo', 'bar') # false

```

#### Convert a base64 encoded string to an uint8 array

```
def base64_to_uint8_array(base64)
  Base64.decode64(base64).bytes
end

base64_to_uint8_array('Zm9vYmFy') # [102, 111, 111, 98, 97, 114]
```

#### Check if a string consists of a repeated character sequence

```
def is_repeated_character_sequence(string)
  string.chars.chunk(&:itself).map(&:last).all? { |x| x.length == 1 }
end

is_repeated_character_sequence('aaaa') # true
is_repeated_character_sequence('aaab') # false

```

#### Convert a string to camelCase

```
def to_camel_case(string)
  string.split('_').map(&:capitalize).join
end

to_camel_case('foo_bar') # 'FooBar'

```

#### Convert a letter to associate emoji

```
def letter_to_emoji(letter)
  letter = letter.downcase
  (letter.ord + 127365).chr(Encoding::UTF_8)
end

letter_to_emoji('a') # '🇦'
letter_to_emoji('b') # '🇧'

```

#### Convert a string to PascalCase

```
def to_pascal_case(string)
  string.split('_').map(&:capitalize).join
end

to_pascal_case('foo_bar') # 'FooBar'

```

#### Convert a string to URL slug

```
def to_slug(string)
  string.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
end

to_slug('Hello World!') # 'hello-world'

```

#### Convert a Windows file path to Unix path

```
def windows_to_unix_path(path)
  path.gsub('\\', '/')
end

windows_to_unix_path('foo\\bar') # 'foo/bar'

```

#### Convert an uint8 array to a base64 encoded string

```
def uint8_array_to_base64(array)
  Base64.strict_encode64(array.pack('C*'))
end

uint8_array_to_base64([102, 111, 111, 98, 97, 114]) # 'Zm9vYmFy'

```

#### Convert camelCase to kebab-case and vice versa

```
def to_kebab_case(string)
  string.gsub(/([a-z])([A-Z])/, '\1-\2').downcase
end

to_kebab_case('fooBar') # 'foo-bar'
to_kebab_case('foo-bar') # 'fooBar'

```

#### Convert snake_case to camelCase

```
def snake_to_camel_case(string)
  string.split('_').map { |x| x.capitalize }.join
end

snake_to_camel_case('foo_bar') # 'FooBar'

```

#### Convert the name of an Excel column to number

```
def excel_column_to_number(column)
  column.upcase.each_char.map { |x| x.ord - 64 }.join.to_i
end

excel_column_to_number('A') # 1
excel_column_to_number('AA') # 27

```

#### Count the number of words in a string

```
def count_words(string)
  string.split(' ').length
end

count_words('I love Ruby!') # 3

```

#### Count the occurrences of a character in a string

```
def count_character(string, character)
  string.count(character)
end

count_character('I love Ruby!', 'o') # 1

```

#### Decapitalize a string

```
def decapitalize(string)
  string[0].downcase + string[1..-1]
end

decapitalize('FooBar') # 'fooBar'

```

#### Get the base URL without any parameters

```
def get_base_url(url)
  url.split('?')[0]
end

get_base_url('https://google.com?q=foo') # 'https://google.com'

```

#### Format a string

```
def format_string(string, *args)
  string % args
end

format_string('I love %s!', 'Ruby') # 'I love Ruby!'
format_string('I love %s and %s!', 'Ruby', 'Python') # 'I love Ruby and Python!'

```

#### Get the file extension from a file name

```
def get_file_extension(file)
  file.split('.').last
end

get_file_extension('foo.rb') # 'rb'

```

#### Get the file name from a URL

```
def get_file_name(url)
  url.split('/').last
end

get_file_name('https://google.com/foo/bar.jpg') # 'bar.jpg'

```

#### Get the length of a string in bytes

```
def get_string_length(string)
  string.bytesize
end

get_string_length('I love Ruby!') # 12

```

#### Get the number of a character in a string

```
def get_character_number(string, character)
  string.chars.count(character)
end

get_character_number('I love Ruby!', 'o') # 1

```

#### Make the first character of a string lowercase

```
def lowercase_first_character(string)
  string[0].downcase + string[1..-1]
end

lowercase_first_character('FooBar') # 'fooBar'

```

#### Normalize file path slashes

```
def normalize_slashes(path)
  path.gsub('\\', '/')
end

normalize_slashes('foo\\bar') # 'foo/bar'

```

#### Prepend a line number to each line of a text document

```
def prepend_line_number(file)
  File.readlines(file).map.with_index { |x, i| "#{i + 1} #{x}" }.join
end

```

#### Remove duplicate lines of a text document

```
def remove_duplicate_lines(file)
  File.readlines(file).uniq.join
end

```

#### Remove spaces from a string

```
def remove_spaces(string)
  string.gsub(' ', '')
end

remove_spaces('I love Ruby!') # 'IloveRuby!'
```

#### Remove empty lines of a text document

```
def remove_empty_lines(file)
  File.readlines(file).reject { |x| x.strip.empty? }.join
end
```

#### Repeat a string

```
def repeat_string(string, count)
  string * count
end

repeat_string('I love Ruby!', 3) # 'I love Ruby!I love Ruby!I love Ruby!'
repeat_string('I love Ruby!', 0) # ''

```

#### Replace all line breaks with br elements

```
def replace_line_breaks(string)
  string.gsub('

', '<br>')
end

replace_line_breaks('I love

Ruby!') # 'I love<br>Ruby!'

```

#### Replace multiple spaces with a single space

```
def replace_multiple_spaces(string)
  string.gsub(/\s+/, ' ')
end

replace_multiple_spaces('I    love   Ruby!') # 'I love Ruby

```

#### Replace the first given number of characters of a string with another character

```
def replace_characters(string, character, count)
  string.gsub(character, '*', count)
end

replace_characters('I love Ruby!', 'o', 1) # 'I l*ve Ruby!'
replace_characters('I love Ruby!', 'o', 2) # 'I l*v* Ruby!'

```

#### Replace all tab characters with spaces

```
def replace_tabs(string, count)
  string.gsub("\t", ' ' * count)
end

replace_tabs("I\tlove\tRuby!", 2) # 'I  love  Ruby!'

```

#### Reverse the order of lines of a text

```
def reverse_lines(file)
  File.readlines(file).reverse.join
end

```

#### Reverse a string

```
def reverse_string(string)
  string.reverse
end

reverse_string('I love Ruby!') # !ybuR evol I

```

#### Sort lines of a text document in the alphabetical order

```
def sort_lines(file)
  File.readlines(file).sort.join
end
```

#### Sort the characters of a string in the alphabetical order

```
def sort_characters(string)
  string.chars.sort.join
end

sort_characters('I love Ruby!') # ' !IbRUVYdeloru'

```

#### Swap case of characters in a string

```
def swap_case(string)
  string.swapcase
end

swap_case('I love Ruby!') # 'i LOVE rUBY!'

```

#### Trim slashes at the beginning and the end of a string

```
def trim_slashes(string)
  string.gsub(/^\/|\/$/, '')
end

trim_slashes('/foo/bar/') # 'foo/bar'
```

#### Trim some character

```
def trim_character(string, character)
  string.gsub(character, '')
end

trim_character('I love Ruby!', '!') # 'I love Ruby'

```

#### Strip ANSI codes from a string

```
def strip_ansi(string)
  string.gsub(/\e\[[\d;]+m/, '')
end

strip_ansi("\e[31mI love Ruby!\e[0m") # 'I love Ruby!'

```

#### Truncate a string at full words

```
def truncate_string(string, length)
  string.length > length ? string[0..length].split(' ')[0..-2].join(' ') + '...' : string
end

truncate_string('I love Ruby!', 5) # 'I...'
truncate_string('I love Ruby!', 10) # 'I love...'

```

#### Trim the file extension from a file name

```
def trim_file_extension(file)
  file.split('.').first
end

trim_file_extension('foo.rb') # 'foo'

```

#### Uppercase the first character of each word in a string

```
def uppercase_first_character(string)
  string.split(' ').map { |x| x.capitalize }.join(' ')
end

uppercase_first_character('I love Ruby!') # 'I Love Ruby!'
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

#### Generate a random boolean

```
def random_boolean
  [true, false].sample
end

random_boolean #=> true
random_boolean #=> false
```

#### Generate a random integer in given range

```
def random_integer(min, max)
  rand(min..max)
end

random_integer(1, 10) #=> 5
random_integer(1, 10) #=> 8

```

#### Generate a random floating point number in given range

```
def random_float(min, max)
  rand(min..max)
end

random_float(1, 10) #=> 5.123
random_float(1, 10) #=> 8.123
```

#### Generate a random hex color

```
def random_hex_color
  "#%06x" % (rand * 0xffffff)
end

random_hex_color #=> "#e6e6e6"
random_hex_color #=> "#e6e6e6"
```

#### Generate a random string from given characters

```
def random_string(length, characters)
  characters = characters.split('') unless characters.is_a? Array
  Array.new(length) { characters.sample }.join
end

random_string(10, 'abc') #=> "bcbabababa"
random_string(10, 'abc') #=> "ababababab"
```

#### Generate a random IP address

```
def random_ip_address
  Array.new(4) { rand(256) }.join('.')
end

random_ip_address # "169.18.119.188"
random_ip_address # "126.122.102.185"
random_ip_address # "233.85.50.36"
```

#### Generate an array of random integers in a given range

```
def random_integers(length, min, max)
  Array.new(length) { rand(min..max) }
end

random_integers(10, 1, 10) #=> [5, 8, 1, 2, 5, 1, 2, 5, 1, 2]
random_integers(10, 1, 10) #=> [5, 8, 1, 2, 5, 1, 2, 5, 1, 2]
```

#### Generate a random sign

```
def random_sign
  [-1, 1].sample
end

random_sign #=> -1
random_sign #=> 1
```

#### Get a random item and remove it from an array

```
def random_item!(array)
  array.delete_at(rand(array.length))
end

array = [1, 2, 3, 4, 5]
random_item!(array) #=> 3
array #=> [1, 2, 4, 5]
```

#### Generate a random string with given length

```
def random_string(length)
  Array.new(length) { ('a'..'z').to_a.sample }.join
end

random_string(10) #=> "tfdhfuklbz"
random_string(10) #=> "cyiezmppoq"
```

#### Get random items of an array

```
def random_items(array, count)
  array.sample(count)
end

array = [1, 2, 3, 4, 5]
random_items(array, 2) #=> [2, 5]
random_items(array, 2) #=> [1, 4]
random_items(array, 2) #=> [3, 5]
```

#### Get a random item from an array

```
def random_item(array)
  array.sample
end

array = [1, 2, 3, 4, 5]
random_item(array) #=> 2
random_item(array) #=> 5
```

#### Pick a random property of an object

```
def random_property(object)
  object.send
  (object.methods.sample)
end

random_property('abc') #=> "a"
random_property('abc') #=> "b"
```

#### Pick random lines from a text document

```
def random_lines(file, count)
  File.readlines(file).sample(count)
end

randomLines(
  `one
  two
  three
  four
  five`,
    2
)

# ['one', 'four']
```

# Contributing♦️

Submit your PR with your favorite line of code.

Please, add the code snippet to the corresponding category.

Don't forget to always show an example of how your one-liner code works!

<i>Inspired by: https://github.com/phuocng/1loc</i>
