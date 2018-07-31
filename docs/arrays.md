description: Arrays are a collection of items. In Ruby, arrays can take a collection of any type. An array is an ordered list of elements. Each element is a reference to some object.

# Arrays

Arrays are a collection of items. In Ruby, arrays can take a collection of any type. An array is an ordered list of elements. Each element is a reference to some object.

# Creating Arrays

To create an a array you use the `[]` symbols. We can create an empty array as follows :

```ruby
irb(main):001:0> array = []
=> []
irb(main):002:0> array.class
=> Array
```

We can also create the array by calling `new` on the `Array` class as follows :

```ruby
irb(main):003:0> array = Array.new
=> []
irb(main):004:0> array.class
=> Array
```

Create an array and specify an initial capacity :

```ruby
irb(main):005:0> array = Array.new(2)
=> [nil, nil]
```

We can create the array and specify the capacity and initial values :

```ruby
irb(main):006:0> array = Array.new(2,0)
=> [0, 0]
```

Create an array with different types as follows :

```ruby
irb(main):008:0> array = ["hello", Module.new, 3.5]
=> ["hello", #<Module:0x007f844e0742f0>, 3.5]
```

Create an array that initialized with two hashes :

```ruby
irb(main):009:0> array = Array.new(2, Hash.new)
=> [{}, {}]
```

We can also use the `{}` to specify the object to initialize the array with as follows :

```ruby
rb(main):011:0> array = Array.new(2){Array.new(2,0)}
=> [[0, 0], [0, 0]]
```

```ruby
%w{1 2 3} # array of strings
%i{one two three} # arrays of symbols
```

## Accessing Array Elements

We use the `[]` to access the array elements. Retrieve the item at position 0 in the array as follows :

```ruby
irb(main):014:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):015:0> array[0]
=> 1
```

Get the last item in the array :

```ruby
irb(main):017:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):018:0> array[-1]
=> 5
```

Retrieve multiple items using a range :

```ruby
irb(main):019:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):020:0> array[0..2]
=> [1, 2, 3]
```

Using alternative syntax as follows :

```ruby
irb(main):024:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):025:0> array[0,3]
=> [1, 2, 3]
```

Instead of using the `[]` we can use methods to access array elements as follows :

```ruby
irb(main):029:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):030:0> array.at(0)
=> 1
```

Returns `nil` if the item is not found as follows :

```ruby
irb(main):031:0> array.at(5)
=> nil
```

The `at` method does not throw an error if the item is not found. Using `fetch` throws an error if the element is not found as follows :

```ruby
irb(main):032:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):033:0> array.fetch(0)
=> 1
```

Throws an error if the item is not found :

```ruby
irb(main):034:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):035:0> array.fetch(5)
IndexError: index 5 outside of array bounds: -5...5
```

## Remove Elements From The Array

Using the `pop` method we can remove the element from the array as the end :

```ruby
irb(main):038:0> array
=> [1, 2, 3, 4, 5]
irb(main):039:0> array.pop
=> 5
irb(main):040:0> array
=> [1, 2, 3, 4]
```

The `shift` removes an element at the beginning of the array :

```ruby
irb(main):042:0> array
=> [1, 2, 3, 4, 5]
irb(main):043:0> array.shift
=> 1
irb(main):044:0> array
=> [2, 3, 4, 5]
```

### Delete a specific value

Using the `delete` method we can delete a specific value from the array as follows :

```ruby
irb(main):060:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):061:0> array.delete(3)
=> 3
irb(main):062:0> array
=> [1, 2, 4, 5]
```

### Delete a value at a position

We can use the `delete_at` method to remove the value at a specific position as follows :

```ruby
irb(main):064:0> array = [1,2,3,4,5]
=> [1, 2, 3, 4, 5]
irb(main):065:0> array.delete_at(1)
=> 2
irb(main):066:0> array
=> [1, 3, 4, 5]
```

### Delete nil array elements

We can use the `compact` method to remove nil array elements as follows :

```ruby
irb(main):070:0> array = [1,nil,2,nil,5]
=> [1, nil, 2, nil, 5]
irb(main):071:0> array.compact
=> [1, 2, 5]
```

## Array Methods

Arrays contains a lot fo methods, here are some interesting ones :

* `length`
* `size`
* `count`
* `first`
* `last`
* `sample`
* `empty?`
* `sort`
* `shuffle`

### Adding elements at the end of the array

We can use the `push` method or the `<<` to add items to the end of the array as follows :

```ruby
irb(main):072:0> [1,2,3].push(4)
=> [1, 2, 3, 4]
```

Using the shift operator :

```ruby
irb(main):073:0> [1,2,3] << 4
=> [1, 2, 3, 4]
```

### Add elements at the beginning

We can add elements to the beginning of the array using `unshift` and `insert` method as follows :

```ruby
irb(main):074:0> [1,2,3,4].unshift(0)
=> [0, 1, 2, 3, 4]
```

Use insert to place the item at a specific position as follows :

```ruby
irb(main):075:0> [1,2,3,4].insert(0,0)
=> [0, 1, 2, 3, 4]
```

## Looping Through An Array

We can loop through the array using iterators and blocks. The `each` iterator method returns each item within the array :

```ruby
irb(main):076:0> [1,2,3,4].each {|item| p item }
1
2
3
4
=> [1, 2, 3, 4]
```

### Loop in reverse

We can use the `reverse_each` to loop in reverse as follows :

```ruby
irb(main):077:0> [1,2,3,4].reverse_each {|item| p item }
4
3
2
1
=> [1, 2, 3, 4]
```

### Produce a new array based on transformation

We can use the `collect` to produce a transformation of some other array along with a block that takes one element and transforms it :

```ruby
[1,2,3,4].map {|x| x ** 2}
```

We could also have used the `map` method. On arrays they produce the same output.


### Run a block for each item in the array

Using the `map` method, we can run a block of code for each item within the array without modifying the original array as follows :

```ruby
irb(main):078:0> [1,2,3].map {|item| item * item }
=> [1, 4, 9]
```

Using the `map!` modifies the original array as follows :

```ruby
irb(main):082:0> array.map! { |item| item * item }
=> [1, 4, 9]
irb(main):083:0> array
=> [1, 4, 9]
```

### Looping with an index

We can loop through the items and also get access to the index using the `each_with_index` as follows :

```ruby
irb(main):086:0> array.each_with_index { |item, index| p "#{index} #{item}" }
"0 1"
"1 4"
"2 9"
=> [1, 4, 9]
```

### Selecting items that match

We can use a block to select items that match a condition within a block as follows :

```ruby
irb(main):090:0> array
=> [1, 4, 9]
irb(main):091:0> array.select {|item| item.even? }
=> [4]
```

We can use the `select!` to modify the original array.

### Rejecting items not matching

We can return items that does not match by using the `reject` method as follows :

```ruby
irb(main):092:0> array
=> [1, 4, 9]
irb(main):093:0> array.reject { |item| item.even? }
=> [1, 9]
```

### Remove item with a condition

We can use the `delete_if` to remove items that match a condition as follows :

```ruby
irb(main):094:0> array
=> [1, 4, 9]
irb(main):095:0> array.delete_if {|item| item.even?}
=> [1, 9]
```

The `delete_if` method is destructive.

## Sorting arrays

You can sort homogeneous arrays of common data types, like strings or numbers, "naturally" by just calling Array#sort:

```ruby
[5.01, -5, 0, 5].sort                           # => [-5, 0, 5, 5.01]
["Utahraptor", "Ankylosaur", "Maiasaur"].sort   # => ["Ankylosaur", "Maiasaur", "Utahraptor"]
```

To sort objects based on one of their data members, or by the results of a method call, use Array#sort_by. This code sorts an array of arrays by size, regardless of their contents:

```ruby
arrays = [[1,2,3], [100], [10,20]]
arrays.sort_by { |x| x.size }       # => [[100], [10, 20], [1, 2, 3]]
```

We can use a code block to define a sort routine :

```ruby
[1, 100, 42, 23, 26, 10000].sort do |x, y|
    x==42 ? 1 : x<=>y
end
# => [1, 23, 26, 100, 10000, 42]
```

Change the sort order an objects :

```ruby
class Animal
    attr_reader :name, :eyes, :appendages
    def initialize(name, eyes, appendages)
        @name, @eyes, @appendages = name, eyes, appendages
    end
    def inspect
        @name
    end
end

animals = [Animal.new("octopus", 2, 8),
            Animal.new("spider", 6, 8),
            Animal.new("bee", 5, 6),
            Animal.new("elephant", 2, 4),
            Animal.new("crab", 2, 10)]
animals.sort_by { |x| x.eyes }
# => [octopus, elephant, crab, bee, spider]
animals.sort_by { |x| x.appendages }
# => [elephant, bee, octopus, spider, crab]
```

If you pass a block into sort, Ruby calls the block to make comparisons instead of using the comparison operator.

### Shuffling an array

In the older Ruby they was no method to shuffle. In the Ruby 2, the method `shuffle` was introduced. Here is a demo of shuffling a deck of cards :

```ruby
class Card
    def initialize(suit, rank)
        @suit = suit
        @rank = rank
    end
    def to_s
        "#{@suit} of #{@rank}"
    end
end

class Deck < Array
    attr_reader :cards
    @@suits = %w{Spades Hearts Clubs Diamonds}
    @@ranks = %w{Ace 2 3 4 5 6 7 8 9 10 Jack Queen King}
    def initialize
        @@suits.each { |suit| @@ranks.each { |rank| self << Card.new(rank, suit) } }
    end
end

deck = Deck.new
deck.collect { |card| card.to_s }
# => ["Ace of Spades", "2 of Spades", "3 of Spades", "4 of Spades", ...] deck.shuffle!
deck.collect { |card| card.to_s }
# => ["6 of Clubs", "8 of Diamonds", "2 of Hearts", "5 of Clubs", ...]
```

## Exercises

1. Loop through the array and only choose the letters :

    ```ruby
    array = ['1', 'a', '2', 'b', '3', 'c']
    ```
The expected output is `a b c`.
2. Make the each of the following characters uppercase, show at least two ways :

    ```ruby
    array = ['a', 'b', 'c']
    ```
3. Remove duplicates from the following array :

    ```ruby
    survey_results = [1, 2, 7, 1, 1, 5, 2, 5, 1]
    ```
    Also try use the set collection. You can find the Set class by adding the Set standard libary as follows :

    ```ruby
    require 'set'
    ```

    Show also the frequency of the duplicate characters.
4. Sum the items of the array :

    ```ruby
    collection = [1, 2, 3, 4, 5]
    ```
5. Sort the array by the frequency of the words in the sentence.
6. Generate a deck of the 52 cards. Use the following start code :

    ```ruby
    suits = %w{Spades Hearts Clubs Diamonds}
    ranks = %w{Ace 2 3 4 5 6 7 8 9 10 Jack Queen King}
    ```
7. Get the smallest and biggest top and bottom 5 of the following array :

    ```ruby
    [1,60,21,100,-5,20,60,22,85,91,4,66]
    ```
8. Find the smallest word in a sentence.
9. Decompose an array with duplicate values into a hash. Use this as sample :

    ```ruby
    raw_data = [ [1, 'a'], [1, 'b'], [1, 'c'],
                    [2, 'a'], [2, ['b', 'c']],
                    [3, 'c'] ]
    ```
    The expected output is as follows :

    ```ruby
    # => {1=>["a", "b", "c"], 2=>["a", ["b", "c"]], 3=>["c"]}
    ```

## Solution

1. We can use the `step` by skipping 2 steps:

    ```ruby
    (0..array.count).step(2) {|i| p array[i + 1] }
    ```
2. The solution is to perform an operation on the array using `map` or `collect` as follows :

    ```ruby
    array.collect {|c| c.upcase }
    array.map {|c| c.upcase }
    ```
    You could do something interesting we havent covered yet using lambdas as follows :

    ```ruby
    upcase = ->(c){ c.downcase } # create a lambda expression
    array.map(&upcase) # pass a lambda into the map.
    ```
3. We can use the `uniq` method to remove duplicates from an array.

    ```ruby
    survey_results.uniq
    ```

    or using a Set as follows :

    ```ruby
    require 'set'

    s = Set.new
    survey_results.each {|c| s.add}
    ```
4. This is one of the many solutions :

    ```ruby
    collection.inject(0) {|sum, i| sum + i} # => 15
    ```
5. We first need to construct a histogram. Then we can use the `sort_by` method as follows :

    ```ruby
    w = "This is a is a is a word is this sentence"
    hist = w.split.inject(Hash.new(0)) {|hash,v| hash[v] += 1; hash }
    w.split.sort_by {|x| [hist[x], x]}
    ```

    And we can sort distinctly as follows :

    ```ruby
    hist.keys.sort_by { |x| [hist[x], x] }
    ```
6. We can just embed an `each` block inside another one.
7. The idea is to sort the list first and then extract the values :

    ```ruby
    l = [1,60,21,100,-5,20,60,22,85,91,4,66] sorted = l.sort
    #The top 5
    sorted[-5...sorted.size] # => [60, 66, 85, 91, 100]
    #The bottom 5
    sorted[0...5]
    # => [-5, 1, 4, 20, 21]
    ```
8. We can use the `min` on the Array and pass in a block for comparison as follows :

```ruby
w = "This is a is a is a word is this sentence"
w.split.min {|x,y| x.size <=> y.size }
```
9. We can build a hash using the first values from the array as follows :

```ruby
hash = Hash.new { |hash, key| hash[key] = [] }
    raw_data = [ [1, 'a'], [1, 'b'], [1, 'c'],
                 [2, 'a'], [2, ['b', 'c']],
                 [3, 'c'] ]
    raw_data.each { |x,y| hash[x] << y }
hash
    
```