---
layout: post
title: "Fingerprint in Arch Linux"
date: 2013-09-22 03:32
comments: true
categories: \*nix
---


{% img /images/myImage/X230.jpg 300 500 X230 %}

X230 is a cool laptop I ever used, not mentioned it backend by Arch Linux. Coolest thing is that it has figerprint device. 
You can just use "right-index-finger" to login into the system without any key pressed. 

{% codeblock Console lang:sh %}
# check device status
lsusb

# you would find something like this below
.............
.............
Bus 003 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
.............

# install related package
pacman -S fprintd

# scan your fingerprint by this interactive command
fprintd-enroll
# follow the instruction, and you are all set

{% endcodeblock %}







