---
layout: post
title: "Octopress on Cygwin"
date: 2014-04-28 13:36:16 +0800
comments: true
categories: Octopress
---

It is painful when you are forced to use Windows as your programming environment.
But there comes a rescuer Cygwin. With Cygwin, you have almost all tools that Unix
have if install properly.

comment out following these lines
{% codeblock In the Rakefile lang:ruby %}
    #if (/cygwin|mswin|mingw|bccwin|wince|emx/ =~ RUBY_PLATFORM) != nil
      #puts '## Set the codepage to 65001 for Windows machines'
      #`chcp 65001`
    #end
{% endcodeblock %}
or you will get failed in the process of `rake generate`

