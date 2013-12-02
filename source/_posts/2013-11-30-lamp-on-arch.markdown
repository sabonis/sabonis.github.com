---
layout: post
title: "LAMP on ARCH"
date: 2013-11-30 12:11
comments: true
categories: arch
---

If you are a web developer, you got to have these packages to be deployed on your ARCH. 
Those who use Windows, just keep playing CIVILIZATION V, no bothers.

Here is how

Installing part
------------
{% codeblock Console lang:bash %}
# update all packages
pacman -Syu;
pacman -S apache php php-apache mariadb
{% endcodeblock %}
Configuring part
----------------
{% codeblock Console lang:bash %}
vi /etc/httpd/conf/httpd.conf
# append following entries
LoadModule php5_module modules/libphp5.so
AddHandler php5-script php
Include conf/extra/php5_module.conf

vi /etc/php/php.ini
# uncomment this line
extension=mysqli.so

# setup mariadb, this is a interactive command, just follow the instruction
sudo mysql_secure_installation

# enable httpd at start-up
sudo systemctl enable httpd && systemctl restart httpd
{% endcodeblock %}

and we are done here.
