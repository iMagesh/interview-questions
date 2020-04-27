## Rails Questions

### 1. Difference between rake db:migrate db:reset and db:schema:load

- **db:migrate** runs (single) migrations that have not run yet.
- **db:create** creates the database
- **db:drop** deletes the database
- **db:schema:load** creates tables and columns within the (existing) database following schema.rb

- **db:setup** does db:create, db:schema:load, db:seed
- **db:reset** does db:drop, db:setup
- **db:migrate:reset** does db:drop, db:create, db:migrate

Typically, you would use db:migrate after having made changes to the schema via new migration files (this makes sense only if there is already data in the database). db:schema:load is used when you setup a new instance of your app.

I hope that helps.

---

UPDATE for rails 3.2.12:

I just checked the source and the dependencies are like this now:

- **db:create** creates the database for the current env
- **db:create:all** creates the databases for all envs
- **db:drop** drops the database for the current env
- **db:drop:all** drops the databases for all envs
- **db:migrate** runs migrations for the current env that have not run yet
- **db:migrate:up** runs one specific migration
- **db:migrate:down** rolls back one specific migration
- **db:migrate:status** shows current migration status
- **db:rollback** rolls back the last migration
- **db:forward** advances the current schema version to the next one
- **db:seed** (only) runs the db/seed.rb file
- **db:schema:load** loads the schema into the current env's database
- **db:schema:dump** dumps the current env's schema (and seems to create the db as well)

* **db:setup** runs db:schema:load, db:seed
* **db:reset** runs db:drop db:setup
* **db:migrate:redo** runs (db:migrate:down db:migrate:up) or (db:rollback db:migrate) depending on the specified migration
* **db:migrate:reset** runs db:drop db:create db:migrate

For further information please have a look at https://github.com/rails/rails/blob/v3.2.12/activerecord/lib/active_record/railties/databases.rake (for Rails 3.2.x) and https://github.com/rails/rails/blob/v4.0.5/activerecord/lib/active_record/railties/databases.rake (for Rails 4.0.x)

### 2. Why do we need a reverse Proxy? (Ngnix or Apache)

They support gzip and also https to http, underlying app server doesn’t support gzip or https

### 3. Explain how Rails works from beginning to end?

Starting from request on the browser

### 4. What is Gemfile and Gemfile.lock?

A. The Gemfile is where you specify which gems you want to use, and lets you specify which versions. The Gemfile.lock file is where Bundler records the exact versions that were installed. This way, when the same library/project is loaded on another machine, running bundle install will look at the Gemfile.lock and install the exact same versions, rather than just using the Gemfile and installing the most recent versions. (Running different versions on different machines could lead to broken tests, etc.) You shouldn’t ever have to directly edit the lock file.
Get more Explanations on Gem file here.

### 5. Why is Active record a smart choice?

A-There are many reasons why Active Record is the smart choice

- Simplified configuration and default assumptions (Convention over Configuration).
- Associations among objects.
- Automated mapping b/w tables and classes and b/w columns and attributes.
- Data Validations.
- Callbacks
- Inheritance hierarchies.
- Direct manipulation of data as well as schema objects.
- Database abstraction through adapters.
- Logging support.
- Migration support.
  Active Record integrated in other emerging frameworks like Merb.

### 6. What is the difference between Web server and App server?

### 7. What is Session and Cookies?

A: Session: are used to store user information on the server side.
cookies: are used to store information on the browser side or we can say client side
Session : say session[:user] = “srikant” it remains when the browser is not closed

### 8. What is a Proc?

Everyone usually confuses procs with blocks, but the strongest rubyist can grok the true meaning of the question.
Essentially, Procs are anonymous methods (or nameless functions) containing code. They can be placed inside a variable and passed around like any other object or scalar value. They are created by Proc.new, lambda, and blocks (invoked by the yield keyword).
Note: Procs and lambdas do have subtle, but important, differences in ruby v1.8.6. However, I wouldn't expect a candidate talk about these nitty-gritty details during an interview. (Kudos to Noah Thorp)

```ruby
# wants a proc, a lambda, AND a block
def three_ways(proc, lambda, &block)
  proc.call
  lambda.call
  yield # like block.call
  puts "#{proc.inspect} #{lambda.inspect} #{block.inspect}"
end

anonymous = Proc.new { puts "I'm a Proc for sure." }
nameless  = lambda { puts "But what about me?" }

three_ways(anonymous, nameless) do
  puts "I'm a block, but could it be???"
end
 #=> I'm a Proc for sure.
 #=> But what about me?
 #=> I'm a block, but could it be???
 #=> #<Proc:0x00089d64> #<Proc:0x00089c74> #<Proc:0x00089b34>
```

### 9. How to call method dynamically

```ruby
[“foo”, “bar”].each do |method|
  MyClass.send(method)
end
```

### 10. How to create a method dynamically

class Message

```ruby
[:hello, :goodbye].each do |method_name|
  define_method method_name do |arg|
    “#{method_name} #{arg}”
  end
end
#irb
Message.instance_methods false #=> [:hello, :goodbye]
Message.new.hello ’emre’ #=> “hello emre”
Message.new.goodbye ’emre’ #=> “goodbye emre”

```

### 11. How to create a custom validation in rails?

### 12. What things we can define in the model?

There are lot of things you can define in models few are:

1. Validations (like validates_presence_of, numeracility_of, format_of etc.)
2. Relationships(like has_one, has_many, HABTM etc.)
3. Callbacks(like before_save, after_save, before_create etc.)
4. Suppose you installed a plugin say validation_group, So you can also define validation_group settings in your model
5. ROR Queries in Sql

### 13. What is observer in rails

Observer classes respond to life cycle callbacks to implement trigger-like behavior outside the original class.
Rails observers are sweet, You can observe multiple models within a single observer
First, you need to generate your observer:
`command – rails g observer Auditor`
observer classes are usually stored in app/models with the naming convention of app/models/audit_observer.rb.
In order to activate an observer, list it in the config.active_record.observers configuration setting in your config/application.rb file.
`config.active_record.observers = :comment_observer, :signup_observer`
Observers will not be invoked unless you define these in your application configuration.
Reference: http://apidock.com/rails/ActiveRecord/Observer

### 14. Difference between render and redirect?

### 15. What is eagerloading

- One way to improve performance is to reduce the number of database queries through eager loading.
- You can know where we need eager loading through “Bullet’ Gem

### 16. How many types of callbacks available in ROR?

- (-) save
- (-) valid
- (1) before_validation
- (2) before_validation_on_create
- (-) validate
- (-) validate_on_create
- (3) after_validation
- (4) after_validation_on_create
- (5) before_save
- (6) before_create
- (-) create
- (7) after_create
- (8) after_save

### 17. Difference between “and” and && in Ruby?

and is the same as && but with lower precedence.

### 18. What is the use of Destructive Method?

Distructive methods are used to change the object value permanently by itself using bang (!) operator.
`sort` returns a new array and leaves the original unchanged.
`sort!` returns the same array with the modification.
The `!` indicates it’s a destructive method. It will overwrite the current array with the new result and returns it.

### 19. What is the use of load and require in Ruby?

The `require()` method is quite similar to `load()`, but it’s meant for a different purpose.
You use `load()` to execute code, and you use `require()` to import libraries.

### 20. How does nil and false differ?

`nil` cannot be a value, where as a `false` can be a value
A method returns `true` or `false` in case of a predicate, other wise `nil` is returned.
`false` is a boolean data type, where as `nil` is not.
`nil` is an object for `NilClass`, where as `false` is an object of for `FalseClass`

### 21. What is the diffence betweet symbol and string

Symbols have two nice properties compared to strings which can save you memory and CPU time
The difference remains in the object_id, memory and process time for both of them when used together at one time
Strings are considered as mutable objects. Whereas, symbols, belongs to the category of immutable
Strings objects are mutable so that it takes only the assignments to change the object information. Whereas, information of, immutable objects gets overwritten

## 22. How do you track the performance of the application

## 23. What will happen on locking a gem in gemfile.lock and performing bundle update

## 24. Write a braces/brackets/parentheses validator.
Let's say:
* '(', '{', '[' are called "openers."
* ')', '}', ']' are called "closers."
Given a string containing brackets [], braces {}, parentheses (), or any combination thereof, write an efficient method that verify all pairs are matched and nested correctly.

Internal Hint: Should use stack. 

