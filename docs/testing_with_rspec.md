description: RSpec is used for unit testing in Ruby.

# Testing with RSpec

RSpec is used for unit testing in Ruby.

### Install RSpec

RSpec comes as a set of gems, install the gem :

```ruby
gem install rspec
```

### Start using RSpec

You can using RSpec by initializing it as follows :

```ruby
rspec --init
```

Run this from the same folder with your code. Now we can run the `rspec` command line tool.

### First Testing

RSpec uses the `describe` and `it` keywords when writing specs.

```ruby
RSpec.describe 'first test' do
 it 'passes' do
    true
 end
end
```

