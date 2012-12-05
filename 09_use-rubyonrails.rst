.. _use_rubyonrails:

#############################
 Ruby on Rails Sample App
############################# 


Basic Ruby Programming Concepts
================================

Ruby Files
-----------

One way to run ruby code is by putting it in a file with a .rb extension, and 
running in the terminal using ``ruby file.rb``.

As a quick demonstration, open a new file, and paste this Ruby code into it: ::

    #!/usr/bin/ruby

    puts 'Hello world'

When you hit the  button in the menu bar, the console will print out Hello world.

IRB
-----------

IRB, or interactive Ruby, is an interactive environment for Ruby scripting. You 
can open an IRB session in your Cloud9 terminal to practice Ruby coding.

+ In Cloud9, open a terminal window.
+ In the terminal, run:   
    ``irb``

Variables 
----------

A variable is a named space in memory that stores some data. 
A variable is identified by its name.
A variable exists within a scope, and is deleted by a garbage collector when it 
is no longer needed.

+ In irb, look for a variable named x:  
    ``x``

Assignment
-----------

To create a variable in ruby, you assign it an initial value:  
    ``x = 1``

The "=" in ruby is known as the assignment operator. It is used like:
``variable_name = variable_value``

Data Types
-----------

The data that is stored in a variable may be one of the following types:

+ Boolean
+ String
+ Integer
+ Decimal / Float
+ Array
+ Hash

The type of data is determined by syntax during assignment. For example:

+ Boolean:  
    ``x = true``  
  Denoted by either the word true or false *without* quotes around it.

+ String:  
    ``x = "This is a string"``
  Denoted by quotes surrounding the value 

+ Integer:
    ``x = 1``
    Denoted by a number without a decimal point

+ Float:
    ``x = 0.1``
  Denoted by a number with a decimal point

+ Array:
    ``x = ["Item 1", "Item 2", "Item 3"]``
  Denoted by square brackets, with multiple values inside separated by commas

+ Hash:
    ``x = {:name => "variable x", :value => 1}``
  Denoted by curly braces enclosing comma-separated key-value pairs

Ruby is a dynamically typed language. That means that changing the value of a 
variable implicitly changes its type, since a variable inherits its data type 
from its value. ::

    x.is_a? Hash
    x = 1
    x.is_a? Hash

Arithmetic
------------------------------------

In Ruby, you can do all of the normal mathematical arithmetic on integer and 
decimal/float variables.

+-------------------+---------------------+-----------------------------------+
| Operation         | Operand             | Sample Syntax                     |
+-------------------+---------------------+-----------------------------------+
| Addition          | ``+``               | ``x + 2``                         |
+-------------------+---------------------+-----------------------------------+
| Subtraction       | ``-``               | ``x - 2``                         |
+-------------------+---------------------+-----------------------------------+
| Multiplication    | ``*``               | ``x * 2``                         |
+-------------------+---------------------+-----------------------------------+
| Division          | ``/``               | ``x / 2``                         |
+-------------------+---------------------+-----------------------------------+
| Modulus           | ``%``               | ``x % 2``                         |
+-------------------+---------------------+-----------------------------------+

Parentheses can be used to enclose a group of operations, just like in regular
math. So: ::

    x = 1
    x - 0 * 2
    Yeilds: 1
    (x - 0) * 2
    Yeilds: 2

The order of operations is the same as in regular math.

Arithmetic + Assignment
-----------------------------------

You can also combine arithmetic and assignment. These operators perform the
given arithmetic operation on the variable, and assign the result of that 
operation to the new value of the variable, replacing the old value. 
For example:

+---------------+---------------+--------------------------------+-------------+
| Operand       | Initial x     | Sample Use                     | Result x    |
+---------------+---------------+--------------------------------+-------------+
| ``+=``        | 1             | ``x += 2``                     | 3           |
+---------------+---------------+--------------------------------+-------------+
| ``-=``        | 3             | ``x -= 2``                     | 1           |
+---------------+---------------+--------------------------------+-------------+
| ``*=``        | 1             | ``x *= 2``                     | 2           |
+---------------+---------------+--------------------------------+-------------+
| ``/=``        | 2             | ``x /= 2``                     | 1           |
+---------------+---------------+--------------------------------+-------------+
| ``%=``        | 1             | ``x %= 1``                     | 0           |
+---------------+---------------+--------------------------------+-------------+

String Concatenation
------------------------------------

If you want to add some data on to a string, you can use the ``+`` for this.

For example, if you want to have a string variable called "formatted_x" 
that uses the value of the integer variable "x" in it:

    ``formatted_x = "$" + x + ".00"``

Note that the string portions to be concatenated are surrounded by quotes, and 
anything not surrounded by quotes represents a variable or method's *value*. 

Also note that if you change the value of x, this *will not* update the value
of formatted_x, since the *value* of x was inserted into formatted_x, not the 
variable itself. If you wanted to auto-update formatted_x every time that x is
changed, you would have to use a method... read on to find out how.

Comparison
------------------------------------

You may sometimes want to compare the value of a variable to something else.
In Ruby, you can do this using the and, or, and is equal to operators:

+-------------------+---------------------+-----------------------------------+
| Operation         | Operand             | Sample Syntax                     |
+-------------------+---------------------+-----------------------------------+
| And               | ``&&``              | ``x && y``                        |
+-------------------+---------------------+-----------------------------------+
| Or                | ``||``              | ``x || y``                        |
+-------------------+---------------------+-----------------------------------+
| Is Equal To       | ``==``              | ``x == y``                        |
+-------------------+---------------------+-----------------------------------+

An example use of the "And"/"Or" comparisons:

"And" and "Or" are used to compare two boolean variables to each other. Say that 
you have these variables which describe a fast food order: ::

    sandwich = "cheeseburger"
    condiments = ["pickles", "mustard", "ketchup"]
    combo = true
    size = "medium"
    drink_upsize = true
    order = {
      :sandwich => sandwich,
      :condiments => condiments,
      :combo => combo,
      :size => size,
      :drink_upsize => drink_upsize
    }

... and you want to know whether this order is a combo with an upsized drink: ::

    combo && drink_upsize

This returns true, but if you set one of those variables equal to false, it does 
not: ::

    drink_upsize = false
    combo && drink_upsize

So you can see that the "And" comparison checks whether both of the given values
are true, and if not, it returns false.

The "Or" comparison checks to see if either one, or both, of the given values is
true, and if not, returns false. So: ::

    combo || drink_upsize

Returns true.

An example use of the "Is Equal to" comparison:

The "Is Equal To" comparison can be used on two values of *any type* to 
determine if they equal each other. ::

  combo == true
  --> true

  combo == drink_upsize 
  --> false

  combo == "true"
  --> false

  sandwich == "burger"
  --> false

WARNING: Do not confuse ``==`` with ``=``!

Conditionals
------------------------------------

###If...Else

Conditional statements are the simplest form of branching in coding. The first 
condtional is the if...else. It's just used to say: if this codition is true, 
do one thing, if it's not, do another thing. For example: ::

    if order[:sandwich] == "cheeseburger"
      puts "You ordered a cheeseburger"
    end

    if order[:sandwich] == "cheeseburger"
      puts "You ordered a cheeseburger!"
    else 
      puts "You didn't order a cheeseburger."
    end
   
So the structure of the if...else is::
    if conditional statement
      code to run if conditional returns true
    else
      code to run if conditional returns false
    end

Notice you always need an "end" after any conditional statement, to let the
interpreter know where the code that belongs to your branch ends. If you don't
have it, you will get an error.

###If...Elsif

Using ``elsif`` (short for "else if", and used only in Ruby) allows you to add 
more than one conditional to the same statement as your if or if...else. 
For example: ::

    if order[:sandwich] == "cheeseburger"
      puts "You ordered a cheeseburger!"
    elsif order[:sandwich] == "burger"
      puts "You ordered a burger!"
    end   

    if order[:sandwich] == "cheeseburger"
      puts "You ordered a cheeseburger!"
    elsif order[:sandwich] == "burger"
      puts "You ordered a burger!"
    else 
      puts "You didn't order a burger at all."
    end   

###Unless

``Unless`` is just the opposite of ``if``. Use it when you want some code to run, 
unless this one particular condition is met. For example: ::

    unless order[:combo] == false
      puts "You get fries and a drink with that sammy!"
    end

    unless order[:drink_upsize]
      puts "You get a" + order[:size] + " fries and drink with that sammy!"
    end

Methods
------------------------------------


Nil and Blank
------------------------------------


Blocks, Loops, Conditionals
------------------------------------

Get User input
------------------------------------

Coding Best-Practices: KISS, DRY
------------------------------------

Put it all together
------------------------------------

See if you can write a ruby script in a .rb file that will take an order when it
is run.

Sample Rails App & Deployment with Heroku
====================================

Rails is the most popular framework for doing web applications with ruby.
Getting a simple web app up and running on ruby and rails is relatively quick
and easy. 


Get a sample rails app
------------------------------------

First, fork your rails sample app on GitHub. Go to:

https://github.com/vstem-davenport/sample_app

...and click the "fork" button.

Now you have a copy of the project on your Github account.

Next, go to your Cloud9 dashboard and click on the project name under "Projects
On Github" in the left sidebar. Then click the "Clone to Edit" button to clone
a copy of the project to your Cloud9 virtual workstation.

Once your project is finished cloning to Cloud9, open the project workspace by 
clicking the "Start Editing" button.

Install RVM
-----------------------------------

In your rails sample app's Cloud9 project workspace, open a Terminal window.
Run: ::

    curl -L https://get.rvm.io | bash -s stable

Once that command finishes, run the following command to check that RVM is 
working, and also choose a ruby version to use in this project: ::

    rvm use 1.9.3

Install Gems
-----------------------------------

In your Cloud9 Terminal, run this command to create a name for the rvm gemset 
that you'll be using for this project: ::

    rvm use --create 1.9.3@rails_sample_app

Run the bundle install command to install all of the gems in your Gemfile: ::

    bundle install

Run the rails app in Cloud9
-----------------------------------

In your rails sample app's Cloud9 Terminal window, run: ::

    rails s -b $IP -p $PORT

That's it! Your rails app will now be running. You can view your running rails 
app at https://<workspacename>.<username>.c9.io.

Deploy to Heroku
-----------------------------------

In the terminal: ::

    c9pm install heroku
    heroku create
    git add . 
    git status
    git commit -m "Initial commit."
    git push
    git push heroku master

see page 10

Intro OOP
===========================

Calling methods on objects
---------------------------




Resources
===========================
https://docs.c9.io/writing_a_ruby_app.html
https://github.com/mhartl/sample_app
http://ruby.railstutorial.org/
http://guides.rubyonrails.org/
https://devcenter.heroku.com