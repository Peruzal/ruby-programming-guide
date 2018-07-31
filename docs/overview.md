description: Overview of the Ruby programming language from 10 000 feet.

# Overview of Ruby

## Everything Is An Object

In Ruby everything is an object. From the IRB shell lets run a couple of examples.

```ruby
irb(main):001:0> 1.odd?
=> true
```

Notice the output is `true`. We are able to call methods on the literal 1.

```ruby
irb(main):002:0> 1.even?
=> false
```

We can also call methods on strings literals as follows :

```ruby
irb(main):003:0> "Hello World".reverse
=> "dlroW olleH"
```

and we can also find the length of the string :

```ruby
irb(main):004:0> "Hello World".length
=> 11
```

## Comments

Comments in Ruby can be single line or multiple line :

* Single line comments start with a `#` symbol.
* Multiple line comments use `=begin` and `=end`

### Single line comment

Anything after the `#` is ignored.

```ruby
# This is an example of a comment
puts "Hello World" # This comment come after a line of code
```

### Multiple line comments

```ruby
=begin
This is an example
of a multiple line comment.
These type of comments are rare
=end
```


## Blocks and Iterators

Iterators are methods that act as loop constructs in Ruby. Blocks are pieces of code without names. When working with Ruby you will encounter blocks and iterators, let see some examples.

```ruby
irb(main):005:0> 1.upto(5)
=> #<Enumerator: 1:upto(5)>
```

The **upto** is an iterator. We can use to count up to the value in brackets. We can can combine the **upto** iterator with a block as follows :

### each iterator

The **each** iterator is used to iterate through a collection.

### Define an array

```ruby
a = [1,2]
=> [1, 2]
```

### Get an iterator

```ruby
irb(main):016:0> a.each
=> #<Enumerator: [1, 2]:each>
```

```ruby
irb(main):017:0> a.map
=> #<Enumerator: [1, 2]:map>
```

### Blocks

We can use **Blocks** in combination with iterators. The blocks are either single line or multiple line.

### Single line blocks

Single line blocks start with **{** and end with **}** e.g ```{ puts "Hello World" }``` is a single line block.

### Multiple line blocks

Multiple line block start with a **do** and finish with and **end** keyword, e.g

```ruby
do
    puts "Hello World"
end
```

With a single line block :

```ruby
1.upto(2) { puts "Hello" }
Hello
Hello
=> 1
```

With a multi-line line block

```ruby
1.upto(2) do
    p "Hello World"
end
```

We can also generate an iterator from a range and use a block on it as follows :

```ruby
irb(main):033:0> (1..2).each { p "Hello World" }
"Hello World"
"Hello World"
=> 1..2
```

### Passing arguments to blocks

We can pass arguments to blocs using the **||** symbols after the first **{** bracket as follows :

```ruby
(1..3).each {|value| p "Hello World #{value}" }
```

Running this in IRB :

```ruby
irb(main):034:0> (1..3).each {|value| p "Hello World #{value}" }
"Hello World 1"
"Hello World 2"
"Hello World 3"
=> 1..3
```

The ```#{}``` is string interpolation in Ruby. In this case the value for ``index`` will be concatenated with the rest of the string.

We can also use the arguments using the multi-line line block syntax as well. The **||** will come after the **do** statement as follows :

```ruby
(1..3).each do |value|
    p "Hello #{value}"
end
```

With IRB :

```ruby
irb(main):035:0> (1..3).each do |index|
irb(main):036:1* p "Hello #{index}"
irb(main):037:1> end
"Hello 1"
"Hello 2"
"Hello 3"
=> 1..3
```

We can get the powers of numbers between 1 and 10 using arguments passed within an iterator as follows :

```ruby
(1..10).map { |i| 2 ** i }
```

In IRB we get the following :

```ruby
irb(main):038:0> (1..10).map { |i| 2 ** i }
=> [2, 4, 8, 16, 32, 64, 128, 256, 512, 1024]
```

The **\*\*** is the mathematical power operator.

### Read a file line by line using block and iterators

We can also take advantage of the **each** iterator and use a block to output the contents of a text file as follows :

```ruby
File.readlines("pgadmin.log").each { |line| p line }
```

The file ```pgadmin.log``` should be in your current directory you are tunning IRB from.

## Modules

Modules are used to define a namespace. This creates a sandbox that groups together methods, classes and constants. They are also included to extended class behavior.

### Create a module

We use the **module** keyword to create a module as follows 

```ruby
module Greeter
    def greet
        puts "Hello World"
    end
end
```

### Include the module in a class

We can now add functionality to a class using the module as follows :

```ruby
class Person
    include Greeter
end
```

using the `include` keyword, we can now include all the functionality provided by the module into the class. Now the `Person` class can now `greet`.


### Instantiate a new Person object

We can now call `greet` method after creating a new `Person` object

```ruby
p = Person.new
p.greet
```

If we run from within IRB, we get the `Hello World` as below :

```ruby
p = Person.new
=> #<Person:0x007ffc4d9ff730>
irb(main):013:0> p.greet
Hello World
```

## Duck Typing

In Ruby, objects are defined by what they can do. The type of an object is defined by its methods and attributes. Objects are not defined by their type.  If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck.

We use the `responds_to?` method to check what methods the object responds to as follows :

```ruby
irb(main):019:0> (1..5).respond_to? :each
=> true
```

We can see the the (1..5) can respond to the `each` method, therefore we can call `each` on the object.