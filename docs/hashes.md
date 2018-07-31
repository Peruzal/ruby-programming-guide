description: Hashes are dictionary style collections that uses key and value pair. There are also known as associative arrays in other languages.

# Hashes

Hashes are dictionary style collections that uses key and value pair. There are also known as associative arrays in other languages.

## Creating Hashes

They are two ways to create a hash in Ruby.

### Create Hash using {}

We can create an empty hash using the `{}` character as follows :

```ruby
2.2.5 :133 > hash = {}
 => {}
2.2.5 :134 > hash.class
 => Hash
```

### Create Hash using Hash.new

We can also create a hash by calling the `new` method on the `Hash` type as follows :

```ruby
2.2.5 :135 > hash = Hash.new
 => {}
2.2.5 :136 > hash.class
 => Hash
```

### Creating with string keys

We can use strings as keys for the hashes as follows :

```ruby
2.2.5 :137 > p = {"name" => "Joseph", "company" => "Peruzal"}
 => {"name"=>"Joseph", "company"=>"Peruzal"}
```

### Creating a hash using symbols for keys

Instead of using strings, we can use symbols for the keys of the hash as follows :

```ruby
2.2.5 :140 > p = { name: "Joseph", company: "Peruzal" }
 => {:name=>"Joseph", :company=>"Peruzal"}
```

The longer way of using symbols is as follows :

```ruby
2.2.5 :142 > p = { :name => "Joseph", :company => "Peruzal" }
 => {:name=>"Joseph", :company=>"Peruzal"}
```

The shorter way will not work with numeric keys.

You can randomly add more keys to the hash by using the `[]` symbols as follows :

```ruby
2.2.5 :142 > p = { :name => "Joseph", :company => "Peruzal" }
 => {:name=>"Joseph", :company=>"Peruzal"}
2.2.5 :143 > p[:location] = "Cape Town"
 => "Cape Town"
2.2.5 :144 > p
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"}
```

### Getting a count of key

We can use the `count` method to find the number of keys within a hash as follows :

```ruby
2.2.5 :144 > p
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"} 
2.2.5 :145 > p.count
```

### Check fo existence of keys

We can check for the existence of keys within a hash with the `has_key?` methods as follows :

```ruby
2.2.5 :147 > p.has_key? :company
 => true
```

Alternatively we can check if a value exists using  the `has_value?` method as follows :

```ruby
2.2.5 :148 > p.has_value? "Joseph"
 => true
```

### Sort keys
 
By default the hash keys are unordered since we can access them directly, we can use the `sort` method to put the keys in alphabetical order as follows :

```ruby
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"}
2.2.5 :150 > p.sort
 => [[:company, "Peruzal"], [:location, "Cape Town"], [:name, "Joseph"]]
```

## Accessing Hash elements

Hash elements are accessed in a similar way as with the arrays, the different is that in a hash we will use a key instead of an index as in arrays. We use the `[]` to access hash elements as follows :

```ruby
2.2.5 :151 > p
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"} 
2.2.5 :152 > p[:name]
 => "Joseph"
```

### Selecting key and values

We can use the `select` method to return the key/value pairs of a hash as follows :

```ruby
2.2.5 :157 > p.select {|key,value| value == "Joseph"}
 => {:name=>"Joseph"}
```

## Looping Through Hash elements

We can loop through the key/value pair of hash elements using the `each` method as follows :

```ruby
2.2.5 :158 > p.each {|key,value| p "#{key} #{value}"}
"name Joseph"
"company Peruzal"
"location Cape Town"
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"}
```

### Loop through each value pair

We can instead loop through each value pair using the `each_value` method as follows :

```ruby
2.2.5 :159 > p.each_value {|v| p v}
"Joseph"
"Peruzal"
"Cape Town"
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"}
```

### Loop through each key

We can also loop through the keys using the `each_key` as follows :

```ruby
2.2.5 :160 > p.each_key {|k| p k}
:name
:company
:location
 => {:name=>"Joseph", :company=>"Peruzal", :location=>"Cape Town"}
```


### Clearing hashes

We can use the `clear` method to clear the contents of the hash as follows :

```ruby
2.2.5 :161 > p.clear
 => {}
```

### Check if hash if empty

We can use the `empty?` method to check if the hash is empty of not as follows :

```ruby
2.2.5 :162 > p.empty?
 => true
```

### Remove keys

We can remove keys at the beginning of the hash by using the `shift` method as follows :

```ruby
2.2.5 :165 > p
 => {:name=>"Joseph", :company=>"Peruzal"}
2.2.5 :166 > p.shift
 => [:name, "Joseph"]
2.2.5 :167 > p
 => {:company=>"Peruzal"}
```

### Merge hashes

We can use the `merge` method to join two hashes together as follows :

```ruby
2.2.5 :179 > person = { first_name: "Joseph", last_name: "Kandi" }
 => {:first_name=>"Joseph", :last_name=>"Kandi"} 
2.2.5 :180 > company = { name: "Peruzal", location: "Cape Town" }
 => {:name=>"Peruzal", :location=>"Cape Town"} 
2.2.5 :181 > person.merge(company)
 => {:first_name=>"Joseph", :last_name=>"Kandi", :name=>"Peruzal", :location=>"Cape Town"} 
```

## Exercise

1. Choose a random value using a weighted value from a list. The higher the value, the higher the chances of choosing the same value. Assign a weight to each value. E.g :

```ruby
marbles = { :black => 51, :white => 17 }
3.times { puts choose_weighted(marbles) }
# black
# white
# black
```

## Solution

1. The following is one way of implementing it :

```ruby
def choose_weighted(weighted)
    sum = weighted.inject(0) do |sum, item_and_weight|
        sum += item_and_weight[1]
    end
    target = rand(sum)
    weighted.each do |item, weight|
        return item if target <= weight
        target -= weight
    end
end

lottery_probabilities = { "You've wasted your money!" => 1000,
                              "You've won back the cost of your ticket!" => 50,
                              "You've won two shiny zorkmids!" => 20,
                              "You've won five zorkmids!" => 10,
                              "You've won ten zorkmids!" => 5,
                              "You've won a hundred zorkmids!" => 1 }
# Let's buy some lottery tickets.
5.times { puts choose_weighted(lottery_probabilities) }
```