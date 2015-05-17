---
layout: post
title: "たのしいRuby 第4版 Reading Notes 0"
date: 2015-05-03 12:30:48 +0800
comments: true
categories: [Reading note]
---

{% img /images/myImage/ruby_v4.jpg 300 225 %}

I bought it three months ago, but never read it once since then.
It is a Chinese-translated edition, because the original book is
written in Japanese, which I am totally not familiar with, not
even a word.
I gonna to read it, write some notes and hope finish this
book in not very long time.

## Basics

"Hello World" is always a best friend of novice.  
I am going to begin my journey of ruby with its basic output functions.

### Standard outputs

``` ruby
=begin
ruby style's multi-line comments.
=end

print("Hello World\n"); #=> Hello World
# note: semicolon is not nesessary. ruby is not JAVA

puts('Hello World') #=> Hello World
# Same as above except "\n" is automatically added at the end of string.

p('Hello World') #=> 'Hello World'
# "p()" is simply output data in its natrual literal form.
```
### Standard outputs revisited

``` ruby
a = 'World'

print("Hello ", a, "\n")
print("Hello #{a}\n")
puts("Hello #{a}")
#=> Hello World
# Three of above have no differences.

```

### Loops

``` ruby
(10.times do |i|
    print(i)
end).times do
    print(i)
end
#=> 01234567890123456789

```

What?  
Yes, that's a use of chain rule, as [`times`](http://ruby-doc.org/core-2.2.2/Integer.html#method-i-times)
is a function that return itself, which is 10.
10 is a instance of [`Fixnum`](http://ruby-doc.org/core-2.2.2/Fixnum.html)
, which is also a subclass of `Integer`.
Let's take look at the big picture of `Numeric` class hiearchy in Ruby.{%fnin%}For more information, see [Ruby Reference](http://ruby-doc.org/core-2.2.2/Numeric.html){%endfnin%}

``` text Class Hiearchy
Numeric
    -> Integer            #-> method "times" lies in.
        -> Fixnum         #-> where 10 comes from.
        -> Bignum
```
### Everything is object

That's ruby, everything is object. Unlike java, there is no primitive type.
You might wondering where `print()` comes from{%fnin%}See this [post](https://robots.thoughtbot.com/io-in-ruby){%endfnin%}.
`IO` is where it comes from. There are three constant, STDIN, STDOUT and STDERR, which is pointed by 
ruby's global variables, $stdin, $stdout and $sterr respectively.  
`print()` is a alias of `$stdout.print()` provided by ruby's `Kernel` module.

``` ruby print() is alias of $stdout.print()
$stdout.print('I am a alias')
# is equivelent to
print('I am a alias')
```
### Array and Hash
Beside `String` and `Numeric` two basic structure, Ruby has two more advanced data structure -
`Array` and `Hash`.
You can think of both as Java's `List`and `Map`.

``` ruby Array
names = ['sabonis', 'sprewell', 'shiren']
#=> ['sabonis', 'sprewell', 'shiren']

mix = ['sabonis', 29]
#=> Ruby supports different types in one container.

# Size of array
names.size()
#=> 3

# Iteration
names.each { |item|
    print(item, '')
}
#=> sabonis sprewell shiren
# {...} is same as "do ... end" block.

```

``` ruby Hash
address = {:city => 'Taipei', :country => 'Taiwan'}

# Iteration
address.each {|key, value|
    puts(key, ' => ', value)
}
#=> city => Taipei
#=> country => Taiwan
```

`:city` is a `Symbol` of ruby, you can think of this as a lightweight 
version of `String`.
{% blockquote Ruby Reference http://ruby-doc.org/core-2.2.0/Symbol.html %}
The same Symbol object will be created for a given name or string for the duration of a program's execution, regardless of the context or meaning of that name.
{% endblockquote %}

Per doc says, there will be one instance of Symbol with same name till program ended.  


## Notes
{%footnotes_list_inline%}
