---
layout: post
title: "How to add a new post on Octopress"
date: 2013-03-02 09:57
comments: true
categories: Octopress
---
Show me how
-------
This post is for my memory-limited brain. Basically, three step needed.

###1. Create a new post.
```
rake new_post\["POST_TITLE"\] #notice the backslash before square brackets
```
New created post file will locate at place like line below. End with *.markdown*.  

###2. Add markdown format stuff here
```
vi PATH_TO_OCTOPRESS/source/_posts/DATE-POST_TITLE.markdown
```

###3. Generate compliled files and push to server you defined before.
```
rake generate && rake deploy
```
And we are done here.
