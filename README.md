# Quick and dirty introduction to Ruby

#### 6. String concatenation.

```ruby
puts 'Hello, ' + 'John'
```

#### 7. Declare a variable and assign a value to it.

```ruby
my_name = 'John'
```

#### 10. String interpolation

Insert string values into another string. Useful for formatting messages.

```ruby
puts "Hello, #{my_name}"
```


#### 13. Everything is an object. 

Objects are instances of classes. Each object has a method named 'class' that reports the name of its class.

```ruby
puts 'Hello'.class
```



#### 19. Converting between integer and string types.

```ruby
puts 'Hello ' + 4
puts 'Hello ' + 4.to_s

puts 5 + '4'
puts 5 + '4'.to_i
```

In this context, ruby automatically converts the value of my_num into a string:

```ruby
my_num = 5
puts "I have #{my_num} kittens."
```

Now you know:

1. Ruby is a dynamically-typed language.
1. A dynamically-typed language determines the appropriate class for each object by examining its contents.
1. You don't have to declare the type or class of variables in a dynamically-typed language.
1. Within certain limits, a dynamically-typed language can convert the type of a variable from one class to another depending on how the variable is used.
1. When ruby can't guess how to convert the type of a variable, you can call a method on the variable to convert it explicitly to another type, provided the particular conversion makes sense. 


#### 20. You can define your own methods.

```ruby
def add (number1, number2)
  result = number1 + number2  
  return result
end

add(2, 3)
```

#### 21. Simplification: Parentheses are optional... 

...except in cases when their absence would confuse the compiler.

```ruby
def add number1, number2
  result = number1 + number2  
  return result
end

add 2, 3
```

When we append another method call to the result of the first method call, we have to enclose the arguments in parentheses so ruby will know where the first expression ends:

```ruby
add(2, 3).class
```

#### 22. Simplification: You don't need a separate variable for the result of a method.

```ruby
def add number1, number2  
  return number1 + number2
end

add 2, 3
```

#### 23. Simplification: You don't always need a 'return' statement.

A ruby method returns the last value it evaluated, whatever that may be. So, you can omit the 'return' statement in most cases.

```ruby
def add number1, number2  
  number1 + number2
end

add 2, 3
```

In the example above, the last expression evaluated in method 'add' is 'number1 + number2', so that is the value returned from the method.

#### 24. If you need to return from the middle of a method, you need a 'return' statement.

```ruby
def add_positive number1, number2
  if number1 < 0
    return "First number can't be negative"
  elsif number2 < 0
    return "Second number can't be negative"  
  else
    number1 + number2
  end
end

add_positive -4, 5
add_positive 4, -5
add_positive 4, 5
```

Now you know:

1. You can define a method in ruby with the 'def' statement.
1. All the statements between the 'def' and the matching 'end' statements are part of the method.
1. A method is part of a class.
1. A method has a name.
1. A method accepts zero or more arguments.
1. A method returns zero or 1 results.
1. When a method doesn't return a value, ruby treats the result as 'nil' (no value).

#### 25. You can process a list of values (array).

```ruby
arr1 = [ 3, 5, 2, 14, 6, -9 ]
puts arr1.class
puts arr1.methods.sort
puts arr1
puts arr1.sort
puts arr1.shuffle
puts arr1.shuffle
```

Arrays can contain other types besides numbers:

```ruby
arr2 = [ 'Rajesh', 'Ping', 'Susan', 'Martina' ]
```

Array elements can be of different types:

```ruby
arr3 = [ 5.25, 'Steven', true, -75 ]
```

#### 26. Access a specific element in an array.

```ruby
puts arr1[2]
```

#### 27. Convert an array into a string.

```ruby
str1 = arr1.to_s

puts arr1[2]
puts str1[2]
```

#### 28. Create an empty array and add elements to it.

```ruby
arr1 = []
puts arr1.length
puts arr1

arr1[0] = 1
puts arr1.length
puts arr1
puts arr1[0]

arr1[2] = 3
puts arr1.length
puts arr1
puts arr1[0]
puts arr1[1]
puts arr1[2]
```

#### 29. Another way to add elements to an array.

```ruby
arr1 = []
arr1 << 1
arr1 << 2
arr1 << 3
puts arr1.length
puts arr1
```

#### 30. Iterating over an array. 

```ruby
arr1 = [1, 2, 3, 4, 5]
arr1.each { |x| puts x }
arr1.each { |x| puts x * 2 }

arr1.each do |x|
  puts x * 2
end
```

#### 31. Arrays within arrays (multidimensional arrays).

```ruby
arr1 = [1, 2, 3]
arr2 = ['foo', 'bar', arr1]

puts arr2[2][1]
```

Now you know:

1. To process a list of values, you can use an array.
1. You can refer to any element in the array by using its index.
1. Array elements can be of any type - include other arrays.
1. Arrays have a method named 'each' that functions as an iterator. You can pass a block of code into 'each', and it will execute that block once for each element in the array.

#### 32. You can store a list of values with keys.

In Ruby this is called a hash. Other languages call the same kind of structure a dictionary, a map, or a list of key-value pairs.

```ruby
hash1 = { 'key1' => 'value1', 'key2' => 'value2' }
```

The keys and values may be any type of object:

```ruby
hash1 = { 'key1' => 'value1', 'key2' => 2, 'key3' => [5, 4, 3] }
```

#### 33. Retrieve an element from a hash by its key.

```ruby
value1 = hash1['key2']
```

This works because ruby stores the hash keys in an array:

```ruby
hash1.keys
hash1.keys[1]
```

Ruby also stores the hash values in an array:

```ruby
hash1.values
hash1.values[1]
```

But it's more convenient to use the keys to retrieve the values.

```ruby
hash1['key2']
```

#### 34. Add elements to a hash.

```ruby
hash1 = {}
hash1['one'] = 1
hash1['two'] = 2
```

#### 35. Merge the contents of two hashes.

```ruby
hash1 = {}
hash1['one'] = 1
hash1['two'] = 2

hash1.merge 'three' => 3, 'four' => 4
hash1
```

#### 36. Process the elements in a hash.

```ruby
hash1.keys.each { |key| puts hash1[key] }
```

```ruby
hash1.keys.each do |key| 
  puts hash1[key]
end  
```

#### 38. Iterators, loops.

```ruby
5.times do |i|
  i * 2
end

[1, 2, 3, 4, 5].each do |i|
  i * 2
end
```

#### 39. Boolean values.

Ruby represents boolean values with 'true' and 'false' objects.

```ruby
true.class
true.methods
false.class
false.methods
```

#### 40. Conditional expressions.

Conditional expressions return true or false values.

```ruby
5 > 4
5 < 4

val1 = 18
val2 = 7 * 3
puts 'val1 is larger' if val1 > val2
puts 'val2 is larger' if val2 > val2

if val1 > val2
  puts 'val1 is larger'
elsif val2 > val1
  puts 'val2 is larger'  
else
  puts 'val1 and val2 are equal'
end
```
