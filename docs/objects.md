description: Ruby comes with a lot of constants that hold various information. Here are some common constants

# Constants

Ruby comes with a lot of constants that hold various information. Here are some common constants :

* ARGF
* ARGV
* DATA
* ENV
* RUBY_*
* STDERR
* STDIN
* STDOUT
* TRUE/FALSE/NIL

### ARGF

`ARGF` is a stream built when passing in a list of files to be processed using arguments to an application. As a file is processed by `ARGF` it is removed from the ARGV array so that it it not re-processed.

ARGF is a stream designed for use in scripts that process files given as command-line arguments or passed in via STDIN.

The arguments passed to your script are stored in the ARGV Array, one argument per element. ARGF assumes that any arguments that aren't filenames have been removed from ARGV. For example:

```ruby
$ ruby argf.rb --verbose file1 file2

ARGV  #=> ["--verbose", "file1", "file2"]
option = ARGV.shift #=> "--verbose"
ARGV  #=> ["file1", "file2"]
```

You can now use ARGF to work with a concatenation of each of these named files. For instance, ARGF.read will return the contents of file1 followed by the contents of file2.

After a file in ARGV has been read ARGF removes it from the Array. Thus, after all files have been read ARGV will be empty.

You can manipulate ARGV yourself to control what ARGF operates on. If you remove a file from ARGV, it is ignored by ARGF; if you add files to ARGV, they are treated as if they were named on the command line. For example:

```ruby
ARGV.replace ["file1"]
ARGF.readlines # Returns the contents of file1 as an Array
ARGV           #=> []
ARGV.replace ["file2", "file3"]
ARGF.read      # Returns the contents of file2 and file3
```

### ARGV

It is an alias of $*. Holds command line arguments

### ARGF

```ruby
#!/usr/bin/env ruby
count = ARGV.count
puts ARGV[0] if count > 0
```

### DATA

Read portions of the code marked with __END__ and ends at the end of the file.

### ENV 

Read environment variables.

```ruby
irb(main):012:0> ENV["HOME"]
=> "/Users/joseph"
```


```ruby
>> ENV.inspect
```

### RUBY_* Constants

Constants hold information about Ruby. Here are some constants :

* RUBY_COPYRIGHT
* RUBY_DESCRIPTION
* RUBY_ENGINE
* RUBY_PATCHLEVEL
* RUBY_PLATFORM
* RUBY_RELEASE_DATA
* RUBY_VERSION
* RUBY_REVISION

## Freezing Objects

Make an object read-only.

```ruby
irb(main):014:0> results = [10, 120, 57]
=> [10, 120, 57]
irb(main):015:0> results.freeze
=> [10, 120, 57]
irb(main):016:0> results.frozen?
=> true
irb(main):017:0> results.pop
RuntimeError: can't modify frozen Array
```

## Object Metadata

We can check object metadata using methods such as `instance_of?` as follows :

```ruby
>> class Person
>>   end
=> nil
>>  p = Person.new
=> #<Person:0x007fad4d0032f8>
>> p1 = Person.new
=> #<Person:0x007fad4c20ed78>
>> p.instance_of? Person
```

### Check instance

We can use the `is_a?` method to check if an object is an instance of the type as follows :

```ruby
>> class Person
>>   end
=> nil
>>  p = Person.new
=> #<Person:0x007fad4d0032f8>
>> p.is_a? Person
=> true
```