description: Ruby provides different ways of loop logic. Many Rubyists prefer using iterators instead of pure loop logic. In this chapter we will discuss the difference between the two.

# Loops and Iterators

## Loop Method

The `loop` constructs loops through a block of code until the condition is false. If you don't put an end condition the loop will run infinitely.

```ruby
i = 0
loop do
    i += 1
    puts "Hello World"
    break if i == 2
end
Hello World
Hello World
=> nil
```

We can continue with the loop by using the `next` keyword as follows :

```ruby
i = 0
loop do
  i += 1
  next if i == 2
  puts i
  break if i == 5
end
```

## While Loop

The syntax for the `while` is :

```ruby
while (boolean condition)
#code statement
end
```

The while will run as long as the condition is true.

```ruby
i = 0
while i < 5
  i += 1
  puts i
end
```

## Until Loop

`until` is the negated form of the `while` statement :

```ruby
i = 0
until i >= 5
  i += 1
  puts i
end
```

The same statement with `while` :

```ruby
i = 0
while i < 5
  i += 1
  puts i
end
```

## While and Until- Alternative Syntax

The `while` statement have alternative syntax. We can put the statement at the beginning of the while statement as follows :

```ruby
i = 0
puts "#{ i += 1 }" while i < 5
```

### until alternative syntax

The `until` also have an alternative syntax as follows :

```ruby
i = 0
puts "#{ i += 1 }" until i == 5
```

### Do..While Alternative Syntax

```ruby
i = 0
begin
  puts i
  i += 1
end while i < 5
```

## For Loop

You can use the traditional `for` loop as in other languages as follows :

```ruby
for i in 1..5
  puts i
end
```

### Alternative `for` statement

An alternative for the `for` statement is to use the `times` methods :

```ruby
5.times {|i| puts i}
```

### Step

We can use a step function to choose th upper boundary in what steps we would like to loop as follows :

```ruby
1.step(10,2) { |i| puts i}
```

### `case` statement

You use the case statement instead of using multiple if/elsif/else statements :

```ruby
lang = "fr"

dog = case lang
  when "en"
    "dog"
  when "es"
    "perro"
  when "fr"
    "chien"
  when "de"
    "Hund"
  else "dog"
end
```

And when using symbols :

```ruby
lang = :de

doggy = case lang
  when :en then "dog"
  when :es then "perro"
  when :fr then "chien"
  when :de then "Hund"
end
puts doggy
```

We can also use ranges with the case statement :

```ruby
scale = 8

out = case scale
  when 0 then "lowest"
  when 1..3; "medium-low"
  when 4..5; "medium"
  when 6..7; "medium-high"
  when 8..9; "high"
  when 10; "highest"
  else "off scale"
end
puts "Scale: " + outs
```

The `;` and `then` are used when we put the statement on the same line. We could have written the same as follows :

```ruby
scale = 8

out = case scale
  when 0
    "lowest"
  when 1..3
    "medium-low"
  when 4..5
    "medium"
  when 6..7
    "medium-high"
  when 8..9
    "high"
  when 10
    "highest"
  else
    "off scale"
end
puts "Scale: " + out
```

We could also use complicated logical operations in the `when` clause.