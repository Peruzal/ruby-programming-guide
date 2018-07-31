description: Errors and exceptions are part of every program. Ruby program methods to catch errors and exceptions in your code.

# Catching Errors and Exceptions

Errors are child classes of `StandardError` class. To catch errors we surround the offending code in `begin` and `rescue` block as follows :

```ruby
begin
  puts 1 / 0 # code that can generate an error
rescue
  puts "Cant divide by Zero" # catch the error here
end
```

### Catching specific exceptions

We can catch specifying their name in the rescue bloc as follows :

```ruby
begin
  file = File.open "nginx.conf"
  puts 1 / 0
rescue StandardError => error # Catch the StandardError
  puts "Cant divide by Zero"
  puts "Error was #{error.class}"
end
```

We can catch more errors in a block, the specific errors first and general at the end as follows :

```ruby
begin
  file = File.open "nginx.conf"
  puts 1 / 0
rescue ZeroDivisionError => error # more specific
  puts "Cant divide by Zero"
  puts "Error #{error.to_s}"
rescue Errno::ENOENT => error # general
  puts "Sorry, we can't open the file specified"
  puts "Error: #{error.to_s}"
end
```

## Raising Exceptions

We raise exceptions by using the `raise` keyword as follows :

```ruby
begin
  raise "Testing an error" # raise and exception
  puts “Shouldn't execute this code"
rescue Exception => error
  puts "Rescued an exception: #{error.inspect}"
end
```

## Creating Our Own Exceptions

We can create custom exceptions by extending from the `StandardError` class as follows :

```ruby
class MyException < StandardError
  
end
```

## Ensure block

We can have a block of code that always runs by using the `ensure` keyword as follows : 

```ruby
begin
  raise "Testing an error" # raise the error
  puts "Shouldnt execute this code"
rescue Exception => error # catch the error
  puts "Rescued an exception: #{error.inspect}"
ensure
  puts "This code will always run" # this code always runs
end
```