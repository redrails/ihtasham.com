---
layout: post
title: 'Seven Languages in Seven Weeks: Ruby, Day 2'
date: '2012-01-29T15:56:00.000-08:00'
author: Yevgeniy Brikman
tags:
- Seven Languages in Seven Weeks
- Software Engineering
modified_time: '2012-02-01T00:45:15.459-08:00'
blogger_id: tag:blogger.com,1999:blog-5422014336627804072.post-108414827713914395
blogger_orig_url: http://brikis98.blogspot.com/2012/01/seven-languages-in-seven-weeks-ruby-day_29.html
---

In my [previous 
post](http://brikis98.blogspot.com/2012/01/seven-languages-in-seven-weeks-ruby-day.html), 
I went through the [Day 1 Ruby 
problems](http://brikis98.blogspot.com/2012/01/seven-languages-in-seven-weeks-ruby-day.html) 
from [Seven Languages in Seven 
Weeks](http://brikis98.blogspot.com/search/label/Seven%20Languages%20in%20Seven%20Weeks). 
Today, I'll share my solutions to the Day 2 problems and some more thoughts 
about Ruby. 

<span style="font-size: x-large;">**Ruby, Day 2: Thoughts** 

I originally learned Ruby (and many other programming languages) the "hacker 
way": that is, I did a 10 minute syntax tutorial, browsed other peoples' code 
a bit, and then just started using the language, looking up missing pieces as 
I went. Although this is the most fun and productive way I've found to get 
started with a language, it can also lead to missing some of the finer points 
and subtleties. 

For example, until the "Ruby, Day 2" chapter, I never had a full appreciation 
for Ruby code blocks and the yield keyword. For example, even though I 
frequently used 
"[times](http://ruby-doc.org/core-1.9.3/Integer.html#method-i-times)" to do 
looping, I never thought deeply about how it worked: 

<script src="https://gist.github.com/1700592.js?file=print_name.rb"></script> 
It turns out that times is just a function (slightly obscured because Ruby 
doesn't require parentheses for function calls) on the Integer class that 
takes a code block as an argument. Times could be implemented as follows: 

<script 
src="https://gist.github.com/1700969.js?file=custom_times.rb"></script> 
This style of coding allows for some powerful possibilities. For example, it 
is surprisingly easy to introduce a "do in a transaction" function: 

<script 
src="https://gist.github.com/1700969.js?file=transaction_wrapper.rb"></script> 
Using this, I can now trivially wrap any number of statements in a 
transaction: 

<script src="https://gist.github.com/1700969.js?file=transaction.rb"></script> 
The equivalent in less expressive languages, such as Java, often involves 
vastly more code, implementing arbitrary interfaces, anonymous inner classes, 
and a lot of very hard-to-read code. For comparison, here is an example of how 
Java's [Spring Framework](http://www.springsource.org/) recommends wrapping 
[JDBC code in 
transactions](http://static.springsource.org/spring/docs/2.5.x/reference/jdbc.html): 


<script 
src="https://gist.github.com/1700969.js?file=SpringTransaction.java"></script> 
<span style="font-size: x-large;">**Ruby, Day 2: Problems** 

The Day 2 problems are only slightly tougher than Day 1. The most fun part was 
coming up with a way to keep the code as concise as possible. 

## <span style="font-size: large;">Print 16 
Print the contents of an Array of 16 numbers, 4 numbers at a time, using just 
"each". Now, do the same with "each_slice" in 
[Enumerable](http://ruby-doc.org/core-1.8.7/Enumerable.html). 

<script 
src="https://gist.github.com/1700969.js?file=each_16.rb"></script><script 
src="https://gist.github.com/1700969.js?file=each_slice_16.rb"></script> 
## <span style="font-size: large;">Tree 
Modify the Tree class initializer (original code 
[here](https://gist.github.com/1700969#file_tree_original.rb)) so it can 
accept a nested structure of Hashes. Trickiest part here was that the 
"collect" function can call the passed in block with either one argument 
that's an Array or two arguments that represent the (key, value) pair. 

<script src="https://gist.github.com/1700969.js?file=tree_new.rb"></script> 
## <span style="font-size: large;">Grep 
Write a simple grep that will print the lines and line numbers of a file 
having any occurrence of a phrase anywhere in that line. 

<script src="https://gist.github.com/1700969.js?file=grep.rb"></script> 
<span style="font-size: x-large;">**Ruby vs. Java, Round 2 ** 

I couldn't resist implementing the grep code in Java to see how it compares: 

<script src="https://gist.github.com/1700969.js?file=Grep.java"></script> 
It's **33 lines long**. The Ruby solution was a one-liner. 

## <span style="font-size: x-large;">Ruby, Continued 
<b> 
</b> 
Check out more Ruby goodness on [Ruby, Day 
3](http://brikis98.blogspot.com/2012/01/seven-languages-in-seven-weeks-ruby-day_31.html). 