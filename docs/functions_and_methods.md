description: Ruby provides an easy way to define methods and functions. Using the def keyword you can define a function that either takes parameter and no parameters at all. In this section we will discuss how to create and call functions.

# Functions and Methods

Enables reusable code. DRY(Don’t Repeat Yourself)

### Defining and Calling Methods

```ruby
def hello
  puts "Hello World"
end
```

### Calling Methods

```ruby
hello
```

or alternatively with braces

```ruby
hello()
```

### Creating methods with parameters

```ruby
def hello(name)
  puts "Hello #{name}"
end
```

and calling the method as follows :

```ruby
hello "Joseph"
hello("Joseph")
```

### Methods with Default Parameters

```ruby
def hello(name="John")
  puts "Hello #{name}"
end
```

### Constructor - Initialize Method

`initialize` is a special method in a class. Its called automatically when an object is created.

```ruby
class Person
  def initialize(name)
    puts "New person created"
  end
end
```

When we create the new `Person` object, the `initialize` method is automatically called as demonstrated below :

```ruby
irb(main):075:0> p = Person.new("Joseph")
New person created
```

### The return statement

Ruby methods do not need to use the `return` keyword. The last expression evaluated will be returned. If a method does not return anything, it returns `nil`.

```ruby
  def hello
    puts “Hello World” #Implicit return
  end
```

We can also explicitly add a return keyword as follows :

```ruby
  def add(n, n1)
    return n + n1
  end
```

We can use it as follows :

```ruby
puts add(1,2)
```


### Returning multiple values

We can also return multiple values as follows :

```ruby
def return_multiple
    return 10, 30.5, 50
end
```

and use the function as follows :

```ruby
n, n1, n3 = return_multiple
```

### Variable parameters

We can use the hash within the parameter list to pass in variable params. Any older way is to use the `\*variable-name`.

Using the hash :

```ruby
def variable_params(opts = {})
    #Do something
end
```

older way :

```ruby
def variable_params(*opts)
 puts opts.count if opts.count > 0
end
```

### Named parameters

We can use symbols to name the name of the params as follows :

```ruby
def full_name(first_name: "John", last_name: "Doe")
 puts "#{first_name} #{last_name}"
end
```

and we can now call the method as follows :

```ruby
full_name(first_name: "Joseph", last_name: "Kandi")
```

### Class methods

We can also have methods inside a class. We use the `self` keyword when defining methods on the class as follows :

```ruby
class Person
  def self.count
    puts "Method on the Person class"
  end
end
```

and we can call the method as follows :

```ruby
Person.count
```


### Sample method signatures with required, optional, and default-valued arguments

![Method Signatures](/images/method-signatures.png)