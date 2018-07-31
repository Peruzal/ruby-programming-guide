description: String very powerful is Ruby. They have a tonne of methods to manipulate the characters.

# String Literals

String literals are surrounded by single or double quotes.

```ruby
> puts "Hello World"
Hello World
```

Double quoted string literals allows for string interpolation. Here is an example with interpolation using double quoted string literals :

```ruby
2.2.5 :076 > puts "Hello World"
Hello World
 => nil
2.2.5 :077 > name = "Joseph"
 => "Joseph"
2.2.5 :078 > puts "Hello #{name}"
Hello Joseph
 => nil
```

interpolation does not work with single quotes :

```ruby
2.2.5 :080 > name = "Joseph"
 => "Joseph" 
2.2.5 :081 > puts 'Hello #{name}'
Hello #{name}
 => nil 
```


### Quoting inside string literlas

We can use single quotes inside double quotes as follows :

```ruby
2.2.5 :082 > puts "Joseph's iPhone"
Joseph's iPhone
 => nil
```

We can use an escape character if we really want the double quote inside the double quoted string literal as follows :

```ruby
2.2.5 :085 > puts "Joseph\"s iPhone"
Joseph"s iPhone
 => nil
```

### Escape Characters

* \" - Escaping  double quote using  backslash
* \\ - Escaping  backslash with another backslash
* \a - Bell/Alert
* \b - Backspace
* \r - Carriage Return
* \n - New Line
* \s - Space
* \t - Tab

### String interpolation

String interpolation allows the substitution of a variable inside a string literal. We us the `#{variable_name}` as follows :

```ruby
2.2.5 :086 > name = "Joseph"
 => "Joseph"
2.2.5 :087 > company = "Peruzal"
 => "Peruzal"
2.2.5 :088 > puts "My name is #{name} and i work at #{company}"
My name is Joseph and i work at Peruzal
 => nil
```

## HERE Doc

We can have multiple lines of string literals by using HERE doc instead of the double or single quotes. A HERE doc start with `<<ANY_WORD_HERE` and end sa new line with `ANY_WORD_HERE`. Here is an example

```ruby
2.2.5 :093 > puts <<END
2.2.5 :094"> This is an example
2.2.5 :095"> of a string that
2.2.5 :096"> spans over multiple lines.
2.2.5 :097"> END
This is an example
of a string that
spans over multiple lines.
 => nil
```

The HERE does starts with `<<END` and finishes with `END`.

## Printing without a new line

To output without adding a new line we use `print` instead of `puts` as follows :

```ruby
2.2.5 :098 > print "Hello World"
Hello World => nil
```

### String delimiters

We can use a character to delimit the start and end of a string as follows :

```ruby
%q*Start and end of character*
```

## String Methods

The String type have a lot of methods, we will look at a subset below :

* `downcase`
* `upcase`
* `capitalize`
* `swapcase`
* `length`
* `empty?`

## Concatenating Strings

We can use the + operator to concatenate strings as follows :

```ruby
2.2.5 :113 > puts "Hello " + "World"
Hello World
 => nil
```

We can concatenate using string interpolation as well :

```ruby
2.2.5 :114 > name = "Joseph"
 => "Joseph"
2.2.5 :115 > puts "My name is #{name}"
My name is Joseph
 => nil
```

### Extracting character from strings

We can use the `[]` to extract character or substrings from a string as follows :

```ruby
2.2.5 :116 > name = "Joseph"
 => "Joseph" 
2.2.5 :117 > name[0]
 => "J"
```

We can also pass a range and extract a substring :

```ruby
2.2.5 :120 > name = "Joseph"
 => "Joseph"
2.2.5 :121 > name[0...3]
 => "Jos"
```

We can also use negative numbers to begin extracting from the end of the string as follows :

```ruby
2.2.5 :122 > name = "Joseph"
 => "Joseph"
2.2.5 :123 > name[-1]
 => "h"
```

### Splitting strings

We use the `split` method to split a string. You will need to choose the character to use to split the string as follows :

```ruby
2.2.5 :126 > full_name.split()
 => ["Josep", "Kandi"]
```

Using a comma to split as follows :

```ruby
2.2.5 :127 > fruits = "Oranges,Apples,Mangoes"
 => "Oranges,Apples,Mangoes"
2.2.5 :128 > fruits.split(",")
 => ["Oranges", "Apples", "Mangoes"]
```

We can split the string directly into variables as follows :

```ruby
2.2.5 :129 > data = "Joseph,Kandi,Peruzal"
 => "Joseph,Kandi,Peruzal"
2.2.5 :130 > first_name,last_name,company = data.split(",")
 => ["Joseph", "Kandi", "Peruzal"]
2.2.5 :131 > first_name
 => "Joseph"
2.2.5 :132 > company
 => "Peruzal"
```

## Regular Expressions

Regular expressions allows for pattern matching. In Ruby they are multiple ways to match a paatern :

* Use the `=~`
* Use `%r{pattern}`
* Use `/pattern/`
* The `Regexp` class
* The `match` method on the String class

### Matching with =~

```ruby
name = "My name is Joseph Kandi"
name =~ /Joseph/ # note that we are providing a pattern using //
=> 11
```

The `=~` will return the starting position of the match.

### Matching with %r{}

We could have written the above as follows :

```ruby
name = "My name is Joseph Kandi"
%r{Joseph} =~ name # note Joseph is not a string but a pattern
=> 11
```

Will return the same result.

### Using the match method

We could also have used the `match` method on the String class as follows :

```ruby
name = "My name is Joseph Kandi"
name.match(/Joseph/) # note Joseph is not a string but a pattern
 => #<MatchData "Joseph">
```

The `match` method returns `nil` if it cant find the match. The match data can be accessed with global variables :

```ruby
2.2.5 :067 > $~ # Match object
 => #<MatchData "Joseph">
2.2.5 :068 > $& # The last match
 => "Joseph"
2.2.5 :069 > $' # pre match
 => " Kandi"
2.2.5 :070 > $` # post match
 => "My name is "
```

$1, $2, etc Contains text matching first, second, etc. capture group.

### Negative match

We can use the `!~` for a negative match :

```ruby
d = "0114804898"
%r{d+} !~ d # one or more digits
=> true # returns true of false
```

### Modifiers (options)

* `/pattern/i` - Ignore case (or constant Regexp::IGNORECASE)
* `/pattern/m` - Treat a newline as a character matched by a full stop or period (.) (or constant Regexp::MULTILINE)
* `/pattern/x` - Ignore whitespace and comments in the pattern (or constant Regexp::EXTENDED)
* `/pattern/o` - Perform #{} interpolation only once

## String Exercises

1. What is the character used for string interpolation?
2. You have the following code and you want to interpolate the variable :

    ```ruby
    number = 50
    # puts "The number is "
    ```
 Use the `number` variable and output `The number is 50` using string interpolation.
3. Show the number after and prior using string interpolation
    ```ruby
    number = 50
    # puts "The number is and prior is and next is"
    ```
4. Reverse the string ".sdrawkcab si gnirts sihT" permanently using a method on the String class.
5. Make the following code snippet read properly by using the `split`, `reverse` and `join` methods on the String class :
    ```ruby
    s = "order. wrong the in are words These"
    ```
6. Why are symbols more preferred than using Strings?
8. Enumerate over the String, "Ruby is awesome" one character at a time. Show two ways of enumerating the String.
9. Show the frequencies of each word in a sentence. Use any sentence.
10. Make the String "Ruby" lowercased.
11. Make all vowels in a sentence uppercase. Show different ways of achieving it.
12. Check if the following String is really a String, "Ruby is a programming language". Hint, use duck typing.
13. Extract the substring "language" from the String "Ruby language". Show two ways.
14. Generate the full aplhabet without typing the characters manually.
15. Generate the full alphabet in reverse order.
16. Write a Ruby snippet to check for a valid email address.
17. Extract the domain name and check if the MX record is valid. Use the code below for validating the domain :

```ruby
Resolv::DNS.new.getresource(hostname, Resolv::DNS::Resource::IN::MX)
```
18. Write Ruby code to check for a valid IP address.
19. Check a string whether is a number, a letter or a mixed set of letters and number.
20. Check is a word is a palindrome or not. Test with the following words :

```ruby
A but tuba
A man, a plan, a canal: Panama
A Santa at Nasa
Anne, I vote more cars race Rome to Vienna
```


## Solution to Exercises

In Ruby they are many ways of doing things, the snippets here are just one way of solving the exercises.

1. The `#{}` is used for string interpolation.
2. By using string interpolation, the code will be :
    
    ```ruby
    number = 50
    puts "The number is #{number}"
    ```
3. The code to show the number before and after is as follows :
   
     ```ruby
    number = 50
    puts "The number is #{number} and prior #{number -1} is and next is #{number.succ}"
    ```

4. The code to reverse permanently is to use the `reverse!` method as follows :
    
    ```ruby
    sentence = ".sdrawkcab si gnirts sihT".reverse!
    ```

5. We first use the `split` method to make the string an array, then reverse the array using the `reverse` method and then join the reversed array using the `join` method.
    
    ```ruby
    s = "order. wrong the in are words These"
    s.split.reverse.join(" ")
    ```

6. There's only one version of the symbols as shown by the code below :

    ```ruby
    :name.object_id # will always return the same object id
    "name".object_id # generates a new object id each time
    "name".object_id # generates a new object id not similar to the previous string
    ```

7. We can use the `scan` method on the string class and use a regex to find all word then iterate through them as follows :

    ```ruby
    s =  "Ruby is awesome"
    s.scan(/\w+/) { |w| puts w}
    ```

    or we could split the string using the `split` method, this turns it into an array and now we can now use the `each` method as follows :
    ```ruby
    s.split().each {|w| p w}
    ```
8.  To generate frequencies we can use a Hash that is initialized with zero values for keys that do not exist using the `Hash.new(0)` as follows :

    ```ruby
    freq = Hash.new(0)
    s = "Show the frequencies of each word in a sentence. Use any sentence"
    s.scan(/\w+/) {|w| freq[w] += 1}
    puts freq
    freq.each {|k,v| p "#{k} #{v}"} # loop through the key and values
    ```
9. We can use the downcase method as follows `"Ruby".downcase`.
10. We can us the `tr` method that translates a character or we can use the global substitution `gsub` methods as follows :

    ```ruby
    s = "Make all vowels in a sentence uppercase."
    s.tr("aeiou", "AEIOU")
    ```
16. Check for a valid email, we can use a regex as follows :

    ```ruby
    email = 'joseph@peruzal.com' # test email address
    valid = '[^@]+' # exclude invlaid character in the email
    email =~ /^#{valid}@#{valid}.#{valid}$/ # validate the email

    valid = '[A-Za-z\d.+-]+' # we could use for commonly encountered email addresses
    ```
17. We can extract the domain and also check for the MX records as follows :

    ```ruby
    require 'resolv'

    def valid_email_host?(email)
        hostname = email[(email =~ /@/)+1..email.length] valid = true
            begin
                Resolv::DNS.new.getresource(hostname, Resolv::DNS::Resource::IN::MX) 
            rescue Resolv::ResolvError
                valid = false
            end
        return valid
    end
    ```
18. We can use the regex together with a case statement as follows :

    ```ruby
    string = "123"
    case string
    when /^[a-zA-Z]+$/
    "Letters"
    when /^[0-9]+$/ "Numbers"
    else
    "Mixed"
    end
    ```