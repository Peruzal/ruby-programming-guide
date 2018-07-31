description: Ruby provides an extensive set of arithmetic, comparison, boolean, range and shift and append operators. Most of the operators in Ruby are implemented as methods, you can call the operators as if you are calling a normal method.

# Ruby Operators

Ruby operators can be broadly categorized into the following : 

* Arithmetic
* Shift or Append
* Comparison
* Booleans
* Ranges

## Arithmetic Operators

The arithmetic operators are :

* **+** - Addition
* **-** - Subtraction
* **\*** - Multiplication
* **\*\*** - Exponential
* **/** - Division
* **%** - Modulo

### Addition

```ruby
> 1 + 1
 => 2
```

### Division

```ruby
> 5 / 2
 => 2
```

To get 2.5 as the answer you will need to use floating point numbers as follows :

```ruby
> 5.0 / 2.0
 => 2.5
```

### Modulo

Remainder division

```ruby
> 5 % 2
 => 1
```

You will get an exception if you try to divide by 0.

```ruby
> 2 /0
ZeroDivisionError: divided by 0
	from (irb):9:in `/'
```

Floating point division with 0 will give `Infinity` as a result.

```ruby
> 2.0 / 0.0
 => Infinity
```

### Addition on Arrays

We can apply addition to arrays, the result in a concatenation of the two arrays as follows :

```ruby
> [1,2] + [3,4,5]
 => [1, 2, 3, 4, 5]
```

### Arithmetic Operators on Strings

We can also apply arithmetic operators on string objects as follows :

```ruby
> "Hello world " * 2
 => "Hello world Hello world "
```

Only the multiplication operator works, other arithmetic operators will produce an error.

### Exponential Operators

We use the **\*\*** for exponent as follows :

```ruby
 > 2 ** 2
 => 4
```

### Shift operators

We can use the two shift operators, << and >>. This allows us to manipulate the numbers in binary. E.g we can easily get a 4 by shifting the 2 in binary by 1 as follows.

```ruby
> 2 << 1
 => 4
```

Here is how it works. The number 2 in binary is represented as 10. When we shift by 1 we push an additional 0 at the end, so we now get the number 100, which is 4 in binary.

We can display the value of 2 in binary using the **to_s(2)** method as follows :

```ruby
> 2.to_s(2)
 => "10"
```

We can see that 2 in binary is 10.

If we change the operator and push to the right, we now remove the leading 0.

```ruby
> 2 >> 1
 => 1
```

We now get a 1 since we removed the leading 0 from 10.

We can shift with more bits if we prefer, e.g. to get the value 8 we can push 2 by 3 bits as follows :

```ruby
> 2 << 2
 => 8
```

### Append Operator

The same operator for left shifting, << is for appending on arrays.

```ruby
> nums = []
 => [] 
2.2.5 :029 > nums << 1
 => [1] 
2.2.5 :030 > nums << 2
 => [1, 2]
```

We could also apply the append multiple times as follows :

```ruby
 > nums << 3 << 4
 => [1, 2, 3, 4]
```

### Output to Standard Output

The << operator is also used to output to Standard Output as follows :

```ruby
 > STDOUT << "Hello World"
Hello World => #<IO:<STDOUT>>
```

## Comparison Operators

* < - Less than operator
* <= - Less then or equal to operator
* > - Greater than operator
* >= - Greater than operator
* <=> - Comparable operator
* != - Not equal to operator

### Comparable operator <=>

The other operators perform exactly as they are supposed to except the comparable operator. The comparable operator works as follows :

* Returns -1 if the left hand value is less than the right hand operand
* Returns 1 if the left hand operand is greater than the right hand operand
* Return 0 is they are equal
* Returns nil if they can not be compared

```ruby
> 2 <=> 2
 => 0
```

```ruby
> 1 <=> 2
 => -1
```

```ruby
> 2 <=> 1
 => 1
```

## Boolean Operators

* && - Logical AND operator
* || - Logical OR operator
* ! - NOT operator

### && operator

The operator returns tru if all the operands are true or false otherwise.

```ruby
> 10 > 0 && 10 < 9
 => false
```

### || operator

The logical OR operator returns true if any of the operands returns true. It returns false if both operands return false.

```ruby
> 10 > 0 || 10 == 10
 => true
```

### ! NOT Operator

Negates the operand.

```ruby
> !true
 => false
```

```ruby
> !false
 => true
```

### ||= OR Equal

This operator returns the current value if its initialized or initializes the new value.

```ruby
> b ||= 5 # b is not defined, so we get 5
 => 5
2.2.5 :049 > b = 10 # assign b to a new value of 10
 => 10
2.2.5 :050 > b ||= 5 # assign 5 if b does not have a value
 => 10 # b have a value so we get the value already assigned
```

Performing the same operation above only using the ||(logical OR) operator results in  an error as follows :

```ruby
 > a || 5
NameError: undefined local variable or method `a' for main:Object
```

## Range Operators

Range operators are used to implement sequences, conditions and intervals.

### Range operator

We define the range with ..(inclusive) or ...(exclusive) operators.


### Inclusive range operator

```ruby
> (1..3).each {|i| p i}
1
2
3
 => 1..3
```

### Exclusive range operator

```ruby
> (1...3).each {|i| p i}
1
2
 => 1...3
```

Verify that the class is a range :

```ruby
> (1..2).class
 => Range
```

### Convert a range to array

We can convert the Range to an array using the `to_a` as follows :

```ruby
> (1..5).to_a
 => [1, 2, 3, 4, 5]
```
### Convert to an enum

We can also convert the range to an enumerable using `to_enum` as follows :

```ruby
 > n = (1..5).to_enum
 => #<Enumerator: 1..5:each>
2.2.5 :060 > n.next
 => 1
2.2.5 :061 > n.next
 => 2
```

We can also create and convert range of type character as follows :

```ruby
> alphabet = ('a'..'z').to_enum
 => #<Enumerator: "a".."z":each>
2.2.5 :065 > alphabet.next
 => "a" 
2.2.5 :066 > alphabet.next
 => "b" 
```
