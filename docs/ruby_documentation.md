description: Ruby have an extensive documentation system. RDoc and ri provide local documentation whilst the https://ruby-doc.org/ and https://www.ruby-lang.org/en/documentation/ website provide online documentation.

# Ruby Documentation

Ruby documentation can be found in the following places :

* RDoc
* ri
* [Ruby doc website](http://ruby-doc.org/)
* [Devdocs.io](http://devdocs.io/ruby~2.4/)
* [Dash App](https://kapeli.com/dash)

## RDoc

RDoc produces HTML and online documentation for Ruby projects. We can use the command line tool `rdoc` to generate Ruby documentation.

## RVM Documentation

```ruby
rvm docs generate
```

## ri documentation from rvm

Generate ri docs without generating rdoc with the following :

```ruby
rvm docs generate-ri
```

## ri

The `ri` command line tool will show Ruby documentation if installed. To show ri documentation for the `String`, you can run the following on the terminal :

```ruby
ri String
```

## Ruby Gems Documentation

You can find documentation on installed gems by running the gems server as follows :

```ruby
gem server
```

You will get a port number on which the gem server is running. Use the browser to access the server.