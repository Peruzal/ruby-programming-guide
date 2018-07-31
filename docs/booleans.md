description: Booleans are used to represent true or false values. In Ruby the true and false are each individual classes. The class for true is TrueClass and the false is FalseClass.

# Booleans

 Booleans are used to represent true or false values. In Ruby the `true` and `false` are each individual classes. The class for true is `TrueClass` and the false is `FalseClass`.

## Creating Booleans

Check the class for `true` and `false` as follows :

```ruby
irb(main):001:0> true.class
=> TrueClass
irb(main):002:0> false.class
=> FalseClass
```

## Expression Trees

Booleans are used in evaluation expressions.

```ruby
>> n = 20
=> 20
>> n >= 20
=> true
```

Additional expression tests :

```ruby
>> name = "Joseph"
=> "Joseph"
>> name == "Prudence" && n > 20
=> false
```

## if statement

We can also use the `if` statement to check for a true of false condition. The `if` statement have the following syntax :

```ruby
if <boolean express>
 #statements here
end
```

for example :

```ruby
if company == "Peruzal"
    puts "Company is #{company}"
end
```

## Negation

The `!` negates the boolean statement :

```ruby
x = false
if !x
 puts "x is false"
end
```

### Multiple tests

We can perform multiple logical operations. The result should be boolean :

```ruby
ruby = "nifty"
programming = "fun"

if ruby == "nifty" && programming == "fun" # using the and operator
 puts "Keep programming!"
end

if ruby=="nifty" and programming=="fun" and weather=="nice" # using the and logical operator
  puts "Stop programming and go outside!"
end

if a == 10 || b == 27 || c = 43 || d = −14 # using the ||(or) logical operator
 print sum = a + b + c + d
end

if ruby == "nifty" or programming == "fun" # using the or logical operator
 puts "Keep programming!"
end
```

### Putting `if` at the end of the statement

For one line `if` statements, you can place the if condition at the end of the statement as follows :

```ruby
puts "Ruby is great" if true
```

### The `else` statement

Add an optional else to execute a statement when if is not true:

```ruby
if x >= y
 puts "x greater than or equal to y"
else
 puts "x is not greater than or equal to y"
end
```

### The `elsif` statement

Use one or more optional `elsif` statements to test multiple statements (ending with an optional else, which must be last):

```ruby
if x == y
 puts "x equals y"
elsif x != y
 puts "x is not equal to y"
elsif x > y
 puts "x is greater than y"
elsif x < y
 puts "x is less than y"
else
 puts "Well, i dont what is x and y is"
end
```

## `unless` statement

The `unless` statement is the negation of an `if` statement.

```ruby
unless company == "Peruzal"
 company = "Unknown"
else
 company = "Peruzal"
end
```

The equivalent `if` statement :

```ruby
if company == "Peruzal"
 company = "Peruzal"
else
 company = "Unknown"
end
```

### Shot unless statement

We can also add the `unless` at the end of the statement as follows :

```ruby
company = ""
puts "I don't know your company" unless company == "Peruzal"
```

### Tenary operator

For short `if` else expression and then assign a variable, we can use the tenary operator `?:` as follows :

```ruby
>> (company.eql?"Peruzal") ? "Yes" : "No"
=> "Yes"
```

We usually assign the value returned to a variable. The ternary operator is a shortened version of the `if-else` construct.
