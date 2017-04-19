---
layout: post
title:  "Controlling LIFX lights from your terminal"
date:   2017-04-19 21:10:00 +1000
categories: review
tags: [dev, lifx, terminal, bash, lights]
---

## Intro
LIFX is a connected home lighting solution that allows you to control all your lights from native phone or windows desktop apps. That’s all well and good, but if you’re like me, you might want to change them without taking your hands off the keyboard, or just to find out a bit more about how they work.

This is a quick guide on how I was able to set up aliases in my terminal to quickly turn on/off my lights and change colours etc. I didn’t delve too deeply into it, but if you finish setting this up, it shouldn’t be much of a stretch to whip up some more interesting functions.

### Gotta go fast!
This also has the added benefit of a faster reaction from the lights on your network, rather than the occasional delay that you may experience using the app, since your terminal will be broadcasting directly at your lights addresses, which is nice :bulb:

## Preparation
The first step to this is to assign some static IP addresses to your lights on your network. This is necessary because the lights do disconnect/reconnect occasionally, and you will need to know the network address of the lights so that you can address them individually (ie. change only one light, rather than all the lights on your network or subnet).

You can do this by googling and following the specific steps for your router, but you should get by with some generic instructions like [How to Set Up a Static IP Address from Your DLink Router](http://blog.dlink.com/mastering-static-ip-addresses-2/). I recommend using consecutive IP addresses just for ease of organisation and memory, going clockwise around your house or room. This makes things easy to debug and makes for less back and forth copy and pasting when setting up code.

## Implementation
The basic setup is:

* Create packet files. These contain the data that you send to the lights, telling them what colour to turn, with what brightness, what delay and over what time. See documentation here: [LIFX LAN Protocol](https://lan.developer.lifx.com/)
* Set up aliases in your `./bashrc`  file that send the packet file of your choice to the light(s) of your choosing
* Become the master of your domain

### Packets
These are the data packets you will be sending to your lights at their static IP addresses. They contain the information that tells your lights what you want them to do, ie. turn on/off, change to colour x, dim to brightness y. Feel free to use the following pre-made packets or look into how to build your own and explore more here: [Building a LIFX Packet](https://lan.developer.lifx.com/docs/building-a-lifx-packet)

The following packets will turn any light on or off that you broadcast them to, depending on the packet that you send. They do not change the colour of the light, for that you will need to do some research of your own! Or read to the end of the post :wink:

##### turnOn.echo
`\x2a\x00\x00\x34\xb4\x3c\xf0\x84\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x01\x0d\x00\x00\x00\x00\x00\x00\x00\x00\x75\x00\x00\x00\xff\xff\xe8\x03\x00\x00`

##### turnOff.echo
`\x2a\x00\x00\x34\xb4\x3c\xf0\x84\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x01\x0b\x00\x00\x00\x00\x00\x00\x00\x00\x75\x00\x00\x00\x00\x00\xe8\x03\x00\x00`

### Bash commands
The basic bash command formula looks like this:
`echo -e "$(cat <PATH_TO_YOUR_PACKET>)" > /dev/udp/<LIGHT_STATIC_IP>/56700`

So the following example would send the ‘turnOn.echo’ packet to the light at your local IP of 10.0.0.8:
`echo -e "$(cat ~/developer/lifx/turnOn.echo)" > /dev/udp/10.0.0.8/56700`

Note: The `56700` port is the standard LIFX port, and does not require any special network setup steps, so just leave that as the port.

I suggest that you create some conveniently named bash aliases for turning all your lights on/off or targeting them individually. I will leave you to develop your own system for this, as this is half the fun!

### Bonus packets
I would strongly suggest learning how to build your own packets if you have the time, it’s quite interesting and will let you do many more things with your lights :) Go to https://lan.developer.lifx.com/docs/building-a-lifx-packet to learn more.

But for those who want some more quick tricks, here are some packets that will turn your lights the standard RGB colours and back to white. A good start to learning more would be to diff these packets and see what changes in each one :wink:

##### red.echo
`\x31\x00\x00\x34\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x66\x00\x00\x00\x00\x00\x00\xff\xff\xff\xff\xac\x0d\x00\x04\x00\x00`

##### green.echo
`\x31\x00\x00\x34\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x66\x00\x00\x00\x00\x55\x55\xff\xff\xff\xff\xac\x0d\x00\x04\x00\x00`

##### blue.echo
`\x31\x00\x00\x34\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x66\x00\x00\x00\x00\xB0\xA3\xff\xff\xff\xff\xac\x0d\x00\x04\x00\x00`

##### white.echo
`\x31\x00\x00\x34\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x66\x00\x00\x00\x00\x55\x55\x00\x00\xff\xff\xac\x0d\x00\x04\x00\x00`
