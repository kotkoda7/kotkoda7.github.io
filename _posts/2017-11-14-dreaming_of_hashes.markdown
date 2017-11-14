---
layout: post
title:      "{Dreaming of Hashes}"
date:       2017-11-14 07:40:07 +0000
permalink:  dreaming_of_hashes
---


In the past couple of weeks I've been suffering from a bad cold. It's hard to sleep at night and my sleeping pattern has gotten weird. Today I even took an afternoon nap. The funny this is that all I remember of that nap is that I was trying to create Hashes. 

Yes Hashes, like in ones in Ruby! {{{{ }}}}

I learned about hashes before, but with all its complexity (nested and all) it seems so intimadating! Am I the only one feeling like this?? Maybe it's just be being sick and not able to concentrate...

Anyway, I seem to be hang up on one tiny part of hashes. Namely, the format they are written. Or I'd say the many ways it can be written. It puzzled me (first). 



Ok let's get down to it and create a simple hash, using strings:

pizza = {
"topping_1" => "cheese",
"topping_2" => "meat"
}

*#=> {"topping1"=>"cheese", "topping2"=>"meat"}*



We can also use symbols instead of strings, which can be written like this:

pizza = {
:topping_1 => "cheese",
:topping_2 => "meat"
}
*#=> {:topping1=>"cheese", :topping2=>"meat"}*



AND we can also leave out the hash-rocket (=>) and place the colon to the other side of the key symbol:
*used in Ruby 1.9*

pizza = {
topping_1: "cheese",
topping_2: "meat"
}
*#=> {:topping1=>"cheese", :topping2=>"meat"}*



And there's yet also another way to do this (simlarly when creating arrays):
*#by creating an empty hash (of strings) and adding key-value pairs to it*

pizza = Hash.new
pizza["topping_1"] = "cheese"
pizza["topping_2"] = "meat"
pizza

*#=> {"topping1"=>"cheese", "topping2"=>"meat"}*



or we can use the same method but by using symbols:

pizza = Hash.new
pizza[:topping_1] = "cheese"
pizza[:topping_2] = "meat"
pizza

*#=> {:topping1=>"cheese", :topping2=>"meat"}*



Alright, I think now as I am looking at it again, it's really not a big deal.

To sum it up: 
- first decide if you want strings or symbols 
  - if symbols do you want to write it with 'hash-rocket' or without 'hash-rocket' (=>)?
- then decide which of the 2 ways you want to create the hash: 
  {  } or Hash.new
	
Yeah that's it!

Still I think you can see why it was once confusing! :)


