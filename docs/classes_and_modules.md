description: Everything in Ruby is an Object. Objects re created from Classes. We are going to look how to define you own classes and create objects from those classes.

# Classes

## What Are Classes

* Classes are blueprints
* Classes have properties
* Classes have methods that define behavior

### Defining a class

We define a class using the `class` keyword as follows :

```ruby
class Car
end
```

## Objects

Objects are created from classes. Objects are created using the `new` method of the class as follows :

```ruby
irb(main):089:0> c = Car.new
=> #<Car:0x007f862f1ce280>
```

The variable `c` is an object of type `Car`.

### Getter methods

Methods that return properties of the class are called `getters`. Here is a getter method :

```ruby
def color
    @color
end
```

### Setter method

The setter is the method that assigns a value to a property. You can define the setter method as follows :

```ruby
def color=(color)
    @color = color
end
```

We can now use the methods to assign and get values of the properties :

```ruby
irb(main):106:0> c = Car.new
=> #<Car:0x007f86310614b8>
irb(main):107:0> c.color = "Blue"
=> "Blue"
irb(main):108:0> c.color
=> "Blue"
```

### Accessing properties

We access the properties of the class using the `.` operator as above.

### Shorthand getter and setters

We can define the getter and setter using the `attr_accessor` keyword. This creates both the getter and accessor methods on the class as follows :

```ruby
class Car
    attr_accessor :color
end
```

We now use the symbols of the properties instead of string or prepending the @ sign on the property name.

And we use them in the same way :

```ruby
c = Car.new

c.color = "Blue"
puts c.color
=> "Blue"
```

## Constructors

Constructors are methods that are automatically run when we create a new object. They are also used to initialize properties of the class :

```ruby
class Person
  attr_accessor :first_name, :last_name

  def initialize(first_name, last_name)
    self.first_name = first_name
    self.last_name = last_name
  end
end
```

### Private Methods

We can use the `private` keyword to mark the method as private.

```ruby
  private def email_reminders()
    puts "This is a private method"
  end
```

We could also add the `private` keyword at the end of the class as follows :

```ruby
  def email_reminders()
    puts "This is a private method"
  end

private :email_reminders
```

Also the methods are marked private, you can still call the private methods using the `send` method of the object :

```ruby
p = Person.new
p.send :email_reminders # assuming the method is defined on Person class
```

## Instance variables

Instance variables are defined using a single `@`. By defining the accessor methods we automatically get an instance variable. We could have modified the constructor as follows :

```ruby
class Person
  attr_accessor :first_name, :last_name

  def initialize(first_name, last_name)
    @first_name = first_name
    @last_name = last_name
  end
end
```

## Class variables

Class variables are defined using `@@` signs. The variables belong to the class not an instance of the object.

```ruby
class Person

 @@total = 0 # should be initialized before use

  def initialize( fname, lname )
    @fname = fname
    @lname = lname
    @@total += 1
  end

  def self.total
    "Total person objects created " + @@total.to_s
  end
end
```

We can now create objects of type Person and then call the `total` method. The method `total` belongs to the class not a specific object because we prefixed it with a `self` keyword.

```ruby
p = Person.new("J", "K")
p2 = Person.new("K", "J")
puts Person.total
```

### Class methods

We can define class methods by using the `self` keyword or we can use the class name. In the above, `total` is a class method.

```ruby
  def self.total
    "Total person objects created " + @@total.to_s
  end
```

We can also define a class method as follows :

```ruby
class Person

 @@total = 0 # should be initialized before use

  def initialize( fname, lname )
    @fname = fname
    @lname = lname
    @@total += 1
  end

  def Person.total
    "Total person objects created " + @@total.to_s
  end
end
```

## Inheritance

In Ruby we use the `<` for inheritance. When a child class inherits from the parent class, it automatically inherits the methods and properties from the parent class :

```ruby
class Name
 attr_accessor :given_name, :family_name
end

class Address < Name
 attr_accessor :street, :city, :state, :country
end

a = Address.new
puts a.respond_to?(:given_name) # => true
```

## Nested Classes

In Ruby, it’s possible to define classes within other classes. These are called nested classes. Nested classes are useful when a class depends on other classes, but those classes aren’t necessarily useful anywhere else. They can also be useful when you want to separate classes into groups of classes rather than keep them all distinct. Here’s an example:

```ruby
class Drawing
  class Line
  end

  class Circle
  end
end
```

You can now create a new Line as follows :

```ruby
line = Drawing::Line.new
```

Instead of using nested class we could also define a module and next the classes inside :

```ruby
module Drawing
  class Line
  end

  class Circle
  end
end
```

and we will create the Line the same way as before :

```ruby
line = Drawing::Line.new
```
