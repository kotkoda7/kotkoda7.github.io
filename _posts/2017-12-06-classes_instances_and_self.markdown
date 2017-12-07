---
layout: post
title:      "Classes, Instances and Self"
date:       2017-12-07 00:54:42 +0000
permalink:  classes_instances_and_self
---


While I thought I understood most intricacies of object orientation I always find myself having to stop and question everything I write. Line by line. Is that an class or instance? Method or variable? Should I use .self? 
Do these all make sense? Really??!!

Ok let's say I have a pond. I actually do! Well, sort of. I have to share (reluctantly), but It's 5 feet from our apartment. 
And yes, it has ducks! Some other visiting birds, too like Blue herons and Sea gulls.

So what do I do to keep track of these wonderful creatures?

Let's start with **classes**:
- create a class (class MyDucks) with a class variable denoted by @@ so we can count our ducks.
- initialize it so it adds one duck to the whole class (MyDucks) when an instance is created
- create a class method that we can call when we want to know how many ducks we have so far.

class MyDucks

@@duck_count = 0

  def initialize

      @@duck_count += 1

  end

  def self.total_number_of_ducks
    
		@@duck_count
		
  end
	
end

We can call it like this: 

puts MyDucks.total_number_of_ducks  
We should get 0 this time as no instance was created.

We can also change the class method with the use interpolation so we get a whole sentence back:
	
	def self.total_number_of_ducks
      "Now we have #{@@duck_count} ducks in the pond."
  end


Now let's get into **instances**:

- Instance variable is denoted with @. It is a variable that exists as long as the object instance exists, and capture 
- Instance methods expose behavior for objects.

So let's add some instance variables to our class like an id number, age, sex and species (that we set as Mallard, as we know our ducks are all Mallards). Add let's an instance method that tells us the duck ID and its sex.

class MyDucks

@@duck_count = 0

  def initialize (id, species='Mallard', age, sex)
      @@duck_count += 1
			@id = id
      @species = species
      @age = age
      @sex = sex
  end

  def self.total_number_of_ducks
		puts "Now we have #{@@duck_count} duck(s) in the pond."
  end
	
	def sex
    puts "Duck with ID:#{@id} is a #{@sex}!"
  end
	
end


To call an instance method, first we have to create an instance:
duck1 = MyDucks.new(123, 3, 'Female')
Let's call it now:
duck1.sex

We get => Duck with ID:123 is a Female!

Let's call the class and see how many ducks we have now:
MyDucks.total_number_of_ducks  
=> we got 1. 

But now if we want to print out the age of duck1. What? We get an error "undefined method `age' for #<MyDucks:0x00561fb1182f50>". What's wrong?

Well, we called a method that doesn't exist or is unavailable to the object. If we want to access the instance variable, we have to create a method that will return the age (create a getter method). Its only job is to return the value in the @age instance variable. Like this:

def age
  @age
end

Another way to do it is by creating an **attr_accessor** :age.  


class MyDucks

 attr_accessor :age

@@duck_count = 0

  def initialize (id, species='Mallard', age, sex)
      @@duck_count += 1
			
			@age = age
			@id = id
      @species = species
      @sex = sex
  end

  def self.total_number_of_ducks
		puts "Now we have #{@@duck_count} duck(s) in the pond."
  end
	
	def sex
    puts "Duck with ID:#{@id} is a #{@sex}!"
  end
	
end

duck1 = MyDucks.new(123, 3, 'Female')   
duck1.sex    => Duck with ID:123 is a Female!
MyDucks.total_number_of_ducks  => Now we have 1 duck(s) in the pond.

Let's try now:
puts duck1.age    =>  3
Perfect!

Now, I'd like to get into one more thung: SELF. 

**What's self?**
- inside of an instance method it references the instance that called the method. Therefore, self.age= is the same as duck1.weight=.
- outside of an instance method it references the class . It can be used to define class methods. 
def self.age=(age) is the same as def GoodDog.age=(age).

We could add a method called self to see what self is like this:

  def what_is_self
    self
  end
	
	if we call what_is_self we get:
	puts duck1.what_is_self => #<MyDucks:0x00564d6f030508>
	
	This means that when an instance method calls self, it is returning the calling object, so in this case the duck1 object. 
	
	The other place we use self in class methods, which we already done when we created the class method to count the ducks. We can also add 'puts self" to see what self is here. Let's see:
	
	def self.total_number_of_ducks
		puts "Now we have #{@@duck_count} duck(s) in the pond."
		puts self   => MyDucks
  end
	
	It returned MyDucks! So it is true, it returns the class itself.
	
	So we have to pay attention because self changes depending on the scope it's defined in!
	

