description: Setting up the development environment for Ruby.

# Installing Ruby on Linux

The easiest way to install Ruby on a Linux machine is to use the Ruby Version Manager(RVM). On the terminal run the following commands:

### Update the packages

```sh
sudo apt-get update
```

### Install tools for development

```sh
sudo apt-get install build-essential make curl
```

### Install RVM and current version of Ruby

```sh
\curl -sSL https://get.rvm.io | bash -s stable --ruby
```

### Reload the configs before start using RVM

```sh
source ~/.rvm/scripts/rvm
```

## Installing Ruby on Mac OS X

OSX comes with Ruby already installed. The version might be outdated. We can run parallel versions os Ruby using RVM.

### Install RVM and latest Ruby version

```sh
\curl -sSL https://get.rvm.io | bash -s stable --ruby
```

### Realod the RVM config

```sh
source ~/.rvm/scripts/rvm
```

### Installing Ruby on Windows

There is an installer available from [here](http://rubyinstaller.org).

## Interactive Ruby Shell

IRB is an interactive Ruby shell.

### Lanuch IRB

From the terminal run

```sh
irb
```

You can also start the irb terminal without a prompt as follows :

```ruby
irb --noprompt
```

You can also use the simple prompt option that does not display a lot of information as follows :

```ruby
irb --simple-prompt
```

You should now be on the IRB prompt. You can type any valid Ruby commands on the shell

```sh
irb(main):001:0> "Howdy Ruby" * 3
```

The output will be shown starting with the `=>` symbol

### Setting Up AutoCompletion from IRB

If there's no auto-complete when you TAB in IRB shell, you can add the following line to the `~/.irbrc` file.

```ruby
require 'irb/completion'
```

### Running Ruby scripts

Instead of using the irb terminal, you can also run ruby from scripts. Add teh following at the beginning of the file :

```ruby
#!/usr/bin/env ruby
```

You can also add the `-w` to show warning as follows :

```ruby
#!/usr/bin/env ruby -w
```

A simple hello world Ruby script can be as follows :

```ruby
# helloworld.rb
#!/usr/bin/env ruby -w
puts "Hello World"
```

Make script file executable as follows :

```ruby
chmod +x helloworld.rb
```

Execute the script

```ruby
./helloworld.rb
```