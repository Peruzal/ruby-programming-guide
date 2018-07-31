description: Ruby provides powerful ways to handle file input and output.

# File Input/Output

We can read from the standard input using the `gets` method as follows :

```ruby
name = gets
Joseph
=> "Joseph\n"
```

To remove the extra newline at the end, we use the `chomp` methods as follows :

```ruby
2.2.5 :200 > name = gets.chomp
Joseph
 => "Joseph"
```

### Manipulating files

We can work with files on the filesystem using the `File` class. `File.open` opens a files, and we can specify the mode in which we need to open the file.

```ruby
>> file = File.open("pgadmin.log", "r") # open the file for reading
=> #<File:pgadmin.log>
>> file.inspect
=> "#<File:pgadmin.log>"
>> file.read
>> file.close
```

### Opening a file for writing

To open the file for writing we specify the `w` mode as follows :

```ruby
>> file = File.open("test.txt", "w")
=> #<File:test.txt>
>> file.puts "Hello Joseph"
=> nil
>> file.close
=> nil
```

### Open file for appending

We use the `a` character to open the file for appending :

```ruby
>> file = File.open("test.txt", "a")
=> #<File:test.txt>
>> file.puts "Hello there"
=> nil
>> file.close
=> nil
```

## Network Input/Output

We can perform low level networking using the `BasicSocket`, `UDPScket` and `TCPSocket` classes.

## Higher Level Network Input/Output

When working with HTTP we can use use libraries to interact with the protocol. We need to require the library `net/http` as follows :

```ruby
require 'net/http'
conn = Net::HTTP.get_response("www.peruzal.com", "/")
=> #<Net::HTTPOK 200 OK readbody=true>
conn.body.scan(/<img src="(.*?)"/) {|img| puts img}
```
