## Ruby Interview Questions

Table of Contents

- [How to generate a random string in Ruby](#how-to-generate-a-random-string-in-ruby)
- [How to check if a specific key is present in a hash or not?](#how-to-check-if-a-specific-key-is-present-in-a-hash-or-not)
- [Ruby function to remove all white spaces?](#ruby-function-to-remove-all-white-spaces)
- [How to understand nil vs. empty vs. blank in Rails (and Ruby)](#how-to-understand-nil-vs-empty-vs-blank-in-rails-and-ruby)
- [How to call shell commands from Ruby?](#how-to-call-shell-commands-from-ruby)
- [What is attr_accessor in Ruby?](#what-is-attr_accessor-in-ruby)
- [Why is it bad style to rescue exception e in Ruby?](#why-is-it-bad-style-to-rescue-exception-e-in-ruby)
- [What does class << self do in Ruby?](#what-does-class--self-do-in-ruby)
- [Obtain keys, values and sum from array](#obtain-keys-values-and-sum-from-array)
- [What is the method to remove leading and trailing whitespaces?](#what-is-the-method-to-remove-leading-and-trailing-whitespaces)
- [Everything (almost) is an object in Ruby. Please explain](#everything-almost-is-an-object-in-ruby-please-explain)
- [Is Ruby statically or dynamically typed? What is static and dynamic typing?](#is-ruby-statically-or-dynamically-typed-what-is-static-and-dynamic-typing)
- [Tell me about getters and setters in Ruby](#tell-me-about-getters-and-setters-in-ruby)
- [What happens when you call a method in Ruby?](#what-happens-when-you-call-a-method-in-ruby)
- [How can you list all routes in an app?](#how-can-you-list-all-routes-in-an-app)
- [What are some Rails design patterns you’ve used?](#what-are-some-rails-design-patterns-youve-used)
- [How does Rails manage database state?](#how-does-rails-manage-database-state)
- [What is the difference between count, length, and size?](#what-is-the-difference-between-count-length-and-size)
- [How have you implemented authorization in the past?](#how-have-you-implemented-authorization-in-the-past)
- [What are callbacks?](#what-are-callbacks)
- [When would you use a before_save vs. after_save callback?](#when-would-you-use-a-before_save-vs-after_save-callback)
- [What are initializers in Rails?](#what-are-initializers-in-rails)
- [What is the difference between delete and destroy?](#what-is-the-difference-between-delete-and-destroy)
- [What is the meaning of “Fat models, skinny controllers”?](#what-is-the-meaning-of-fat-models-skinny-controllers)
- [What is the meaning of “skinny controllers, skinny models”?](#what-is-the-meaning-of-skinny-controllers-skinny-models)
- [What is the difference between class methods and instance methods?](#what-is-the-difference-between-class-methods-and-instance-methods)
- [What is a PORO?](#what-is-a-poro)
- [Does Ruby allow multiple inheritances?](#does-ruby-allow-multiple-inheritances)
- [Is Ruby strongly or weakly typed?](#is-ruby-strongly-or-weakly-typed)
- [What frameworks have you used for backgrounding jobs?](#what-frameworks-have-you-used-for-backgrounding-jobs)
- [How to declare a constructor on a Ruby class?](#how-to-declare-a-constructor-on-a-ruby-class)
- [What logic goes into a helper?](#what-logic-goes-into-a-helper)
- [When do we use “self” in Ruby?](#when-do-we-use-self-in-ruby)
- [What is Rack?](#what-is-rack)
- [What is MVC?](#what-is-mvc)
- [What is a block in Ruby?](#what-is-a-block-in-ruby)
- [What is the difference between a proc and a lambda?](#what-is-the-difference-between-a-proc-and-a-lambda)
- [What is yield in Ruby?](#what-is-yield-in-ruby)
- [What is content_for for?](#what-is-content_for-for)
- [What is the difference between Hash and JSON?](#what-is-the-difference-between-hash-and-json)
- [What is Active Job?](#what-is-active-job)
- [What is Spring?](#what-is-spring)
- [What is the asset pipeline?](#what-is-the-asset-pipeline)
- [What is the splat operator?](#what-is-the-splat-operator)
- [What is the difference between include and extend?](#what-is-the-difference-between-include-and-extend)
- [What is the difference between load and require?](#what-is-the-difference-between-load-and-require)
- [What is the difference between a class and a module?](#what-is-the-difference-between-a-class-and-a-module)
- [What’s a scope?](#whats-a-scope)
- [What is the difference between class and instance variables?](#what-is-the-difference-between-class-and-instance-variables)
- [What is the difference between find, find_by, and where in ActiveRecord?](#what-is-the-difference-between-find-find_by-and-where-in-activerecord)
- [What is the difference between select, map, and collect?](#what-is-the-difference-between-select-map-and-collect)
- [Define a route for a create action without using “resources”](#define-a-route-for-a-create-action-without-using-resources)
- [What are the three levels of access control?](#what-are-the-three-levels-of-access-control)
- [How do you use singletons in Ruby?](#how-do-you-use-singletons-in-ruby)

### How to generate a random string in Ruby

```ruby
(0...8).map { (65 + rand(26)).chr }.join
```

I spend too much time golfing.

```ruby
(0...50).map { ('a'..'z').to_a[rand(26)] }.join
```

And a last one that's even more confusing, but more flexible and wastes fewer cycles:

```ruby
o = [('a'..'z'), ('A'..'Z')].map(&:to_a).flatten
string = (0...50).map { o[rand(o.length)] }.join
```

### **How to check if a specific key is present in a hash or not?**

`session.key?("user")`

### Ruby function to remove all white spaces?

If you want to remove only leading and trailing whitespace (like PHP's trim) you can use `.strip`, but if you want to remove all whitespace, you can use `.gsub(/\s+/, "")` instead .

### **How to understand nil vs. empty vs. blank in Rails (and Ruby)**

`.nil?` can be used on any object and is true if the object is nil.

`.empty?` can be used on strings, arrays and hashes and returns true if:

```
String length == 0
Array length == 0
Hash length == 0
```

Running `.empty?` on something that is nil will throw a NoMethodError.

That is where `.blank?` comes in. It is implemented by Rails and will operate on any object as well as work like `.empty?` on strings, arrays and hashes.

```
nil.blank? == true
false.blank? == true
[].blank? == true
{}.blank? == true
"".blank? == true
5.blank? == false
0.blank? == false
```

`.blank?` also evaluates true on strings which are non-empty but contain only whitespace:

```
"  ".blank? == true
"  ".empty? == false
```

Rails also provides `.present?`, which returns the negation of `.blank?`.

Array gotcha: blank? will return false even if all elements of an array are blank. To determine blankness in this case, use all? with blank?, for example:

```
[ nil, '' ].blank? == false
[ nil, '' ].all? &:blank? == tru
```

![alt Ruby nil](./images/ruby-nil.png)

### **How to call shell commands from Ruby?**

This explanation is based on a commented [Ruby script][1] from a friend of mine. If you want to improve the script, feel free to update it at the link.

First, note that when Ruby calls out to a shell, it typically calls `/bin/sh`, _not_ Bash. Some Bash syntax is not supported by `/bin/sh` on all systems.

Here are ways to execute a shell script:

      cmd = "echo 'hi'" # Sample string that can be used

1.  <code>Kernel#\`</code> , commonly called backticks – <code>\`cmd\`</code>

    This is like many other languages, including Bash, PHP, and Perl.

    Returns the result (i.e. standard output) of the shell command.

    Docs: http://ruby-doc.org/core/Kernel.html#method-i-60

              value = `echo 'hi'`
              value = `#{cmd}`

2.  Built-in syntax, `%x( cmd )`

    Following the `x` character is a delimiter, which can be any character.
    If the delimiter is one of the characters `(`, `[`, `{`, or `<`,
    the literal consists of the characters up to the matching closing delimiter,
    taking account of nested delimiter pairs. For all other delimiters, the
    literal comprises the characters up to the next occurrence of the
    delimiter character. String interpolation `#{ ... }` is allowed.

    Returns the result (i.e. standard output) of the shell command, just like the backticks.

    Docs: http://www.ruby-doc.org/docs/ProgrammingRuby/html/language.html

            value = %x( echo 'hi' )
            value = %x[ #{cmd} ]

3.  `Kernel#system`

    Executes the given command in a subshell.

    Returns `true` if the command was found and run successfully, `false` otherwise.

    Docs: http://ruby-doc.org/core/Kernel.html#method-i-system

          wasGood = system( "echo 'hi'" )
          wasGood = system( cmd )

4.  `Kernel#exec`

    Replaces the current process by running the given external command.

    Returns none, the current process is replaced and never continues.

    Docs: http://ruby-doc.org/core/Kernel.html#method-i-exec

          exec( "echo 'hi'" )
          exec( cmd ) # Note: this will never be reached because of the line above

Here's some extra advice:
`$?`, which is the same as `$CHILD_STATUS`, accesses the status of the last system executed command if you use the backticks, `system()` or `%x{}`.
You can then access the `exitstatus` and `pid` properties:

            $?.exitstatus

For more reading see:

- http://www.elctech.com/blog/i-m-in-ur-commandline-executin-ma-commands
- http://blog.jayfields.com/2006/06/ruby-kernel-system-exec-and-x.html
- http://tech.natemurray.com/2007/03/ruby-shell-commands.html

        [1]: http://gist.github.com/4069

### **What is attr_accessor in Ruby?**

Let's say you have a class `Person`.

```ruby
class Person
end

person = Person.new
person.name # => no method error
```

Obviously we never defined method `name`. Let's do that.

```ruby
class Person
  def name
  @name # simply returning an instance variable @name
  end
end

person = Person.new
person.name # => nil
person.name = "Dennis" # => no method error
```

Aha, we can read the name, but that doesn't mean we can assign the name. Those are two different methods. The former is called _reader_ and latter is called _writer_. We didn't create the writer yet so let's do that.

```ruby
class Person
  def name
  @name
  end

  def name=(str)
    @name = str
  end

end

person = Person.new
person.name = 'Dennis'
person.name # => "Dennis"
```

Awesome. Now we can write and read instance variable `@name` using reader and writer methods. Except, this is done so frequently, why waste time writing these methods every time? We can do it easier.

```ruby
class Person
  attr_reader :name
  attr_writer :name
end
```

Even this can get repetitive. When you want both reader and writer just use accessor!

```ruby
class Person
  attr_accessor :name
end

person = Person.new
person.name = "Dennis"
person.name # => "Dennis"
```

Works the same way! And guess what: the instance variable `@name` in our person object will be set just like when we did it manually, so you can use it in other methods.

```ruby
class Person
  attr_accessor :name

  def greeting
    "Hello #{@name}"
  end

end

person = Person.new
person.name = "Dennis"
person.greeting # => "Hello Dennis"
```

That's it. In order to understand how `attr_reader`, `attr_writer`, and `attr_accessor` methods actually generate methods for you, read other answers, books, ruby docs.

### **Why is it bad style to `rescue exception => e` in Ruby?**

**TL;DR**: Use `StandardError` instead for general exception catching. When the original exception is re-raised (e.g. when rescuing to log the exception only), rescuing `Exception` is probably okay.

`Exception` is the root of [Ruby's exception hierarchy](http://rubylearning.com/images/exception.jpg), so when you `rescue Exception` you rescue from _everything_, including subclasses such as `SyntaxError`, `LoadError`, and `Interrupt`.

Rescuing `Interrupt` prevents the user from using <kbd>CTRL</kbd><kbd>C</kbd> to exit the program.

Rescuing `SignalException` prevents the program from responding correctly to signals. It will be unkillable except by `kill -9`.

Rescuing `SyntaxError` means that `eval`s that fail will do so silently.

### **What does class << self do in Ruby?**

First, the `class << foo` syntax opens up `foo`'s singleton class (eigenclass). This allows you to specialise the behaviour of methods called on that specific object.

```ruby
a = 'foo'
class << a
  def inspect
    '"bar"'
  end
end
a.inspect   # => "bar"

a = 'foo'   # new object, new singleton class
a.inspect   # => "foo"
```

---

Now, to answer the question: `class << self` opens up `self`'s singleton class, so that methods can be redefined for the current `self` object (which inside a class or module body is the class or module _itself_). Usually, this is used to define class/module ("static") methods:

```ruby
class String
  class << self
    def value_of obj
      obj.to_s
    end
  end
end

String.value_of 42   # => "42"
```

This can also be written as a shorthand:

```ruby
class String
  def self.value_of obj
    obj.to_s
  end
end
```

Or even shorter:

```ruby
def String.value_of obj
  obj.to_s
end
```

---

When inside a function definition, `self` refers to the object the function is being called with. In this case, `class << self` opens the singleton class for that object; one use of that is to implement a poor man's state machine:

```ruby
class StateMachineExample
  def process obj
    process_hook obj
  end

private
  def process_state_1 obj
    # ...
    class << self
      alias process_hook process_state_2
    end
  end

  def process_state_2 obj
    # ...
    class << self
      alias process_hook process_state_1
    end
  end

  # Set up initial state
  alias process_hook process_state_1
end
```

So, in the example above, each instance of `StateMachineExample` has `process_hook` aliased to `process_state_1`, but note how in the latter, it can redefine `process_hook` (for `self` only, not affecting other `StateMachineExample` instances) to `process_state_2`. So, each time a caller calls the `process` method (which calls the redefinable `process_hook`), the behaviour changes depending on what state it's in.

### Obtain keys, values and sum from array

```ruby
arr = [
  [
    {"a" => 10},{"b" => 20},{"c" => 30}],
    [
      {"x" => 40},{"y" => 50},{"z" => 60}
    ]
  ]
]
```

How can you obtain the following?
a)one array containing all keys
b)another array containing all values
c)another array the sum of all the values

Ans: Merge all arrays into single Hash and assign to var ans
ans.keys # will return all keys
ans.values # will return all values
ans.values.inject(:+) # will return the sum of all values

### What is the method to remove leading and trailing whitespaces?

`.strip`

### Everything (almost) is an object in Ruby. Please explain

In object-oriented programming, an object is an instance of a class. In Ruby, all classes are instances of the class `Class`.

For example:

```ruby
7.class => Fixnum
7.class.class => Class
```

A few things are not objects like blocks, methods, and conditional statements (i.e.: if, else).

This question is asked to see if you understand that most things in Ruby behave similarly, which makes Ruby easier to pick up than other languages.

### Is Ruby statically or dynamically typed? What is static and dynamic typing?

Ruby is dynamically typed. This is why you can change the type of a variable on the fly.
In Ruby, the following lines of code, run one after the other, do not throw an error.

```ruby
x = 1
x = "foo"
```

### Tell me about getters and setters in Ruby

A getter allows accessing an instance variable. A setter allows setting an instance variable.
It’s possible to manually define getter and setter methods.

```ruby
class Car
  def color
    @color
  end
  def color=(color)
    @color = color
  end
end
c = Car.new
c.color = 'red'
puts c.color # => red
```

But Ruby provides three accessor methods that do the same thing and are cleaner: `attr_reader` (getter), `attr_writer` (setter), and `attr_accessor` (setter and getter).

```ruby
class Car
  attr_accessor :color
end
c = Car.new
c.color = 'blue'
puts c.color #=> blue
```

### What happens when you call a method in Ruby?

A message containing the method’s name is sent to the object. If that method exists on the object, the object calls it.

This is more apparent if considering Ruby’s send method.

```ruby
obj.hello # => 'hello'
obj.send(:hello) # => 'hello'
```

### How can you list all routes in an app?

`$ rake routes`

It’s also possible to append to this, `| grep <keyword>`, to filter returned routes.

### What are some Rails design patterns you’ve used?

There are a number of design patterns in Rails including service objects, value objects, form objects, query objects, view objects, policy objects, and decorators.

Digging into each one is the topic of a full post but here is a [great tutorial](https://www.sitepoint.com/7-design-patterns-to-refactor-mvc-components-in-rails/) with examples.

### How does Rails manage database state?

The developer manually generates and adds instructions to migration files.

These instruct `ActiveRecord` how to modify the existing database state. For this reason, deleting or modifying previous migrations can put the database into a bad state and is not recommended.

Manually creating migration files is in contrast to other frameworks like Django, where the end state of the database is specified and then migrations are auto-generated to make the required changes.

### What is the difference between count, length, and size?

- `count`: Executes an SQL query to count the number of records. This is useful if the number of records may have changed in the DB vs. memory.

- `length`: Returns the number of items in a collection in memory. It’s lighter weight than count because no database transaction is performed. It can also be used to count characters in a string.

- `size`: This is an alias for length and does the same thing.

### How have you implemented authorization in the past?

Authorization (not to be confused with authentication) pertains to allowing different types of users different levels of access in an app. It’s useful when there are lots of types of users with differing levels of access.

A few gems like `Pundit` and `CanCanCan` implement authorization.

### What are callbacks?

“Callback” is a misleading term. They are hooks into the object lifecycle on which you can execute methods.

A number of callbacks exist around creating, updating, and destroying an object such as `before_validation`, `after_save`, and `after_destroy`.

They are useful for conditional logic like creating an associated Contact record when a `User` record is created.

### When would you use a before_save vs. after_save callback?

Updating an object after it’s been saved requires an additional database transaction to persist the update. So, if you are updating an object’s attribute, a `before_save` callback is more efficient.

But sometimes information does exist on the object until it’s persisted (i.e.: `id`). So, if an `id` is required to create an associated record, that would have to be performed in an `after_save` callback.

### What are initializers in Rails?

Initializers hold configuration logic and only run when an app is booted. This means the Rails server needs to be restarted if initializers are changed. They exist in the `/config/initializers` directory.

### What is the difference between delete and destroy?

- `delete`: Deletes a record.

- `destroy`: Deletes a record and executes callbacks.

The most common callback on `destroy` in Rails apps is specified on associations in model files. For example, the below destroys related `comments` when an `article` is destroyed.

```ruby
class Article < < BaseController
  has_many :comments, dependent: :destroy
end
```

### What is the meaning of “Fat models, skinny controllers”?

Business logic should exist in models, not controllers. This makes logic easier to unit test and is more re-usable.

Controllers are merely the hands that pass information between views and models.

This is generally given as advice to new Rails developers. It’s not actually recommended, particularly in large apps.

### What is the meaning of “skinny controllers, skinny models”?

As a codebase grows, fat models get out of hand, start doing too many things and become unmanageable. Models should handle persistence without being bloated with logic.

Models can be made skinnier by keeping the single responsibility principle in mind and moving logic out of models, and into other design patterns like service objects.

### What is the difference between class methods and instance methods?

Class methods are available on classes, and instance methods are available on instances (of course).They are typically used for different purposes.

For a class, `Article`, an instance method may count the number of words in the body of a specific article. While a class method may count the number of articles by a particular writer across all articles (notice the difference in scope?).

Class methods are denoted by `def self.method_name`.

```ruby
class Greeting
  def self.hello_from_class
    puts 'class: hello'
  end
  def hello_from_instance
    puts 'instance: hello '
  end
end
# class method
Greeting.hello_from_class # => 'class: hello'
# instance method
g = Greeting.new
g.hello_from_instance # => instance: hello
```

### What is a PORO?

PORO stands for “Plain Old Ruby Object”.

Although almost everything in Ruby is an object, `ActiveRecord` tends to use a lot of complex objects. So, the term PORO is typically to stress a small, simple object used to support business logic.

### Does Ruby allow multiple inheritances?

Ruby does not allow inheriting from more than one parent class, but it does allow module mixins with `include` and `extend`.

### Is Ruby strongly or weakly typed?

Ruby is strongly typed. An error will be thrown if you try to calculate `“hello” + 3`.

In contract, JavaScript is weakly typed and would simply evaluate the same calculation to `“hello3”`.

### What frameworks have you used for backgrounding jobs?

**Delayed::Job:** Easy to set up and use. Queues are stored in a database table. If the same database is used for Delayed::Job and production, then a large number of jobs could turn the database into a bottleneck.

**Sidekiq**: Uses Redis to queue jobs. Redis is an in-memory data store so it’s very fast. Sidekiq adds complexity to infrastructure because Redis needs to be added.

**Sucker Punch**: Runs as a Ruby process and keeps all jobs in memory. Jobs are lost if the process crashes. Not recommended for critical tasks.

### How to declare a constructor on a Ruby class?

A constructor is defined via an `initialize` method which is called when a new instance of a class is initialized. Defining this method is not required. It’s often used to provide attribute values on new instances.

```ruby
class Thing
  attr_reader :name
  def initialize(name)
    @name = name
  end
end
t = Thing.new('dog')
puts t.name # => 'dog
```

### What logic goes into a helper?

Helper logic should support views only.

A good candidate for a helper is date formatting logic required in several different views.

### When do we use “self” in Ruby?

- Use `self` when defining and calling class methods.
- In a class, `self` refers to the current class so it’s required when a class method calls another class method.
- `self.class.method` is required when an instance calls a class method.

```ruby
class Adder
  def self.call(*num)
    num.inject(:+)
  end
end
# class method being called by class
puts Adder.call(1,2,3) # => 6
```

### What is Rack?

Rack is an API sitting between the web server and Rails. It allows plugging in and swapping frameworks like Rails with Sinatra, or web servers like Unicorn with Puma.

### What is MVC?

MVC (Model-View-Controller) is a software design pattern that Rails is built around. It splits the handling of information into three pieces.

The model manages data and logic. The view displays information. The controller takes input and prepares data for a model or view

### What is a block in Ruby?

A block is the code between two braces, {…}, or between do and end. You’re passing a block every time you call .each.

Blocks have their own scope and variables only defined inside a block are not accessible outside. But variables defined outside a block can be modified inside a block.

```ruby
{|x| puts x} # a block
```

### What is the difference between a proc and a lambda?

Both procs and lambdas are stored blocks but syntax and behavior differs slightly.
A lambda returns from itself but a proc returns from the method it’s inside.

```ruby
def method_proc
  thing  = Proc.new { return 1}
  thing.call
  return 2
end
def method_lambda
  thing  = lambda { return 1}
  thing.call
  return 2
end
puts method_proc # => 1
puts method_lambda # => 2
```

Notice that `method_proc` returns `1` because calling the proc ends execution within the method.

### What is yield in Ruby?

yield accesses a block passed to a method. It’s typically used in layout files in a Rails application.

```ruby
def puts_stuff
 puts 'first line'
 yield if block_given?
 puts 'third line'
 yield if block_given?
end
puts_stuff { puts 'its me' }
# => first line
# => its me
# => third line
# => its me
```

Notice the `“its me”` is printed when `yield` is called.

### What is content_for for?

It allows defining and rendering content in views. This is useful for defining content in one place and rendering it in many.

### What is the difference between Hash and JSON?

`Hash` is a Ruby class, a collection of key/value pairs that allows accessing values by keys.

`JSON` is a string in a specific format for sending data.

### What is Active Job?

Allows creating background jobs and queuing them on a variety of back ends like Delayed::Job or Sidekiq.

It’s typically used to execute code that doesn’t need to be executed in the main web thread. A common use case is sending notification emails to users.

### What is Spring?

Spring is an application preloader. It keeps the application running in the background so booting is not required any time you run a migration or rake task.

### What is the asset pipeline?

It’s a framework that prepares JavaScript and CSS for the browser.

### What is the splat operator?

Splat is used when you don’t want to specify the number of arguments passed to a method in advance. Ruby has two splat operators, the single splat and double splat.

The single splat works as you’d expect:

```ruby
def do_sth(*input)
  input.each {|x| puts x }
end
do_sth(3,4,5)
# => 3
# => 4
# => 5
```

The double splat is like the single splat but it takes key/values as arguments.

```ruby
def do_sth(**input)
  input.each {|k,v| puts v }
end
do_sth('a':3, 'b':4, 'c':5)
# => 3
# => 4
# => 5
```

### What is the difference between include and extend?

Both are mixins that allow injecting code from another module.

But `include` allows accessing that code via class methods, while `extend` allows accessing that code via instance methods.

```ruby
module Greetings
  def hello
    puts 'hello'
  end
end
module Farewells
  def bye
    puts 'bye'
   end
end
class Conversation
  extend Greetings
  include Farewells
end
# class method
Conversation.hello
# => hello
# instance method
c = Conversation.new
c.bye
# => bye
```

### What is the difference between load and require?

- `load` runs another file, even if it’s already in memory.
  `require` will only run another file once, no matter how many times you require it.

### What is the difference between a class and a module?

- A class has attributes and methods. You can create an instance of a class.
- A module is just a collection of methods and constants, which you can mixin with another module or class.

### What’s a scope?

A scope is `ActiveRecord` query logic that you can define inside a model and call elsewhere.

Defining a scope can be useful rather than duplicating the same logic in many places in the app.

```ruby
# an example scope
class Post
  scope :active_posts, -> { where(active:true) }
end
```

### What is the difference between class and instance variables?

Instance variables denoted by `@,` are associated with an instance of a class. Changing the value of an attribute on one instance has no effect on the variable for another instance.

Class variables denoted by `@@,` are less intuitive. They are shared across all instances of a class. So, changing the variable on one instance affects that variable for all instances.

```ruby
class Coffee
  @@likes = 0
  def like
    @@likes += 1
  end
  def likes
    puts @@likes
  end
end
coffee_one = Coffee.new
coffee_two = Coffee.new
coffee_one.like
coffee_two.like
coffee_one.likes
=> 2
```

Notice how the class variable can be updated by any instance of the class.

### What is the difference between find, find_by, and where in ActiveRecord?

- find: Takes a single argument and looks up the record where the primary key matches that argument.

- find_by: Takes key/values and returns the first matching record.

- where: Takes key/values and returns a collection of matching records. Or an empty collection if there are no matches.

### What is the difference between select, map, and collect?

All three methods take a block as an argument.

- `select`: Is used to grab a subset of a collection. Calling .select! with a bang mutates the original collection.

```ruby
i = [1,2,3,4,5]
i.select {|x| x % 2 == 0}
# => [2, 4]
```

- `map`: Performs an action on each element of a collection and outputs an updated collection. Calling .map! with a bang mutates the original collection.

```ruby
i = [1,2,3,4,5]
i.map {|x| x+1}
# => [2,3,4,5,6]
```

- `collect`: Is an alias of .map and does the same thing.

### Define a route for a create action without using “resources”

-With resources: `resources :photos`.
-Without resources: `post ‘/photos’, to: ‘photos#create’, as: :create_photo`.

### What are the three levels of access control?

- `public`: Any object can call this method.
- `protected`: Only the class that defined the method and its subclasses can call the method.
- `private`: Only the object itself can call this method.

### How do you use singletons in Ruby?

A singleton is a design pattern that only allows a class to have one instance. This is typically frowned upon in Ruby, but Ruby does come with a module for it.

```ruby
require 'singleton'
class Thing
  include Singleton
end
puts Thing.instance
# => #<Thing:0x00007fdd492cf488>
```
