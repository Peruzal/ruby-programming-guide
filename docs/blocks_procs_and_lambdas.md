description: Blocks are methods without names. They are usually used together with iterators. The blocks starts with a do and finish with an end.

# Block, Procs and Lambdas

Blocks are methods without names. They are usually used together with iterators. The blocks starts with a `do` and finish with an `end`. Alternatively blocks use curl braces `{}`.

```ruby
[1,2,3,4].each do |n|
    puts n
end
```

using curly braces for blocks :

```ruby
[1,2,3,4].each { |n|
    puts n
}
```

### Yield keyword

Pass control between a method and block and back as required. The `yield`  executes the block associated with the method.

If we run the we call a method without a block an error will be thrown :

```ruby
def no_block
 yield
end
:no_block
```

and calling the method without a block yield an error :

```ruby
no_block
LocalJumpError: no block given (yield)
	from (irb):2:in `no_block'
```

Define another method and call the method with a block :

```ruby
def block_demo
yield
end
```

And calling the method with a block yields the right result :

```ruby
block_demo { puts "Hello World" }
=> Hello World
```

Lets run some code in the block and in the method as follows :

```ruby
 def hello
   puts "In the Method"
   yield
   puts "Back in the method"
   yield
 end
```

and using it as follows :

```ruby
hello { puts "You are in the block" }
```

We can also access parameters from the block as follows :

```ruby
def hello
  puts "Hello Person"
  yield "Joe"
  puts "Hello Person"
  yield "Peter"
end
```

and calling as follows :

```ruby
hello {|name| puts "Hello #{name}"}
```

We can also check if the block is provided or not as follows :

```ruby
def hello
  puts "Hello Person"
  yield "Joe", "Bloggs" if block_given?
  puts "Hello Person"
  yield "Peter", "Pan" if block_given?
end
```

and calling the method as follows :

```ruby
hello {|first_name, last_name| puts "Hello #{first_name} #{last_name}"}
```

### Passing blocks into methods

Blocks can be used as parameters into a method. The parameter should be preceded with `&` character as follows :

```ruby
def my_iterator(x, &b)
  i = 0
  while(i < x)
    b.call(i*x) # Use call with block parameter
    i += 1
  end
end
```

We can invoke the block code by using the method `call` on the block variable. We can use use the block as follows :

```ruby
my_iterator(5){|x| p x}
```

Note that the parameter needs to be the last argument in the method.


## Procs

A block that can be stored to a variable and executed

```ruby
times_two = Proc.new do |n|
  n * 2
end
```

and using it :

```ruby
puts [1,2, 3].collect(&times_two)
# The & convert the Proc to a block
```

We can also call the Proc directly using the `call` method as follows :

```ruby
times_two.call 4
```

## Lambdas

Same as Procs but uses alternative syntax

```ruby
def lambda_test(my_lambda)
  puts "Method here"
  my_lambda.call
end
```

and using it :

```ruby
lambda_test(lambda {puts "Lambda here"})
```