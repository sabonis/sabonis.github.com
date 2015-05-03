---
layout: post
title: "Hello Sinatra"
date: 2015-04-21 23:09:57 +0800
comments: true
categories: [Hello series]
---

##The setup

I choose to take recently most popular technology - Docker as our testing environment.
One of benefit features of docker is that by using Dockerfile we have a descriptive and
vcs-capable system environment, and that makes our life easier when we have migration needs.

```sh  Project Structure
/PROJECT_HOME/
├── Dockerfile
└── myapp.rb

0 directories, 2 files
```
Easy enough, just two files.  

```dockerfile Dockerfile
# It’ll need ruby
FROM ruby:latest

MAINTAINER sabonis <sabonis.tw@gmail.com>

# The directory our main program` runs on.
VOLUME /server

# Relative path in which command executes.
WORKDIR /server

# Install sinatra
RUN gem install sinatra

# Defaut host of sinatra app is 127.0.0.1,
# that is not OK if your server needs port-forwarding.
CMD ruby myapp.rb -o 0.0.0.0

EXPOSE 4567
```

```ruby myapp.rb
#myapp.rb
require 'sinatra'

get '/' do
  'Hello world!'
end
```
## The Hello

```bash Console
# Build dockerfile to docker image.
sudo docker build -t YOUR_NAME/sinatra

# Run the image.
sudo docker run -dp 80:4567 \
                -v `pwd`:/server \
                YOUR_NAME/sinatra

# Test whether it works.
curl localhost
Hello world!%
#It works.
```
