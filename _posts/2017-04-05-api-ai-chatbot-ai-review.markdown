---
layout: post
title:  "API.Ai Chatbot AI Review"
date:   2017-04-05 13:20:00 +1000
categories: review
tags: [machine learning, chatbot, api.ai, review]
---

## Overview
[API.Ai](https://api.ai/) is Google’s flavour of chat bot, imbued with Natural Language Processing and some AI right off the bat, available to start for free. This project was initially developed by a third party team as a personal assistant AI before being acquired by Google.

It is a great, robust way to get started quickly and inexpensively with a chat bot that can augment or perhaps replace the UI of your application or business.

I would highly recommend it particularly for small businesses or projects, and definitely for hackathon products. It is fast and easy to implement for web applications, and otherwise very developer-friendly.

Any comparisons I make in this post will be to a competitor in the space, IBM Watson, as I didn’t find enough evidence of difference with other competitors to be bothered exploring Wit AI (Facebook) or LUIS (Microsoft).

## Pros & Cons

### Good
* Easy integration with other channels and services (Slack, FB, Text etc)
* All agent logic sits in one place, and can be opened up to a great number of incoming channels and user interfaces.
* Simple editor, easy for non-devs to work with
* Pre-loaded with knowledge and ability on small talk (Free) and a host of other areas (paid)
* Very quick to set up with numerous libraries (I used JS)
* Able to use web hooks to interact easily with your (or any public) API
* Flexible implementation
* Good documentation for most regular use cases
* Easily able to train the bot by correcting intent matches
* Easily clone agents by exporting/importing training data (For backups or test environments)

See the [API.Ai sales page](https://api.ai/) for a more comprehensive list of features and support capabilities.

### Bad
* Not as secure or ready for enterprise level implementation (compared to competitor Watson, IBM)
* Not able to host your own instance of your agent (would be helpful for enterprise solutions to ensure data security)

## When to use
It might be a good idea to look at using API.Ai if:

* You want to get up and running quickly (Hackathons? Side projects?)
* You want  quick and easy integrations with Facebook, Slack, Twitter, Twilio, Skype and more
* You don’t want to build an interface into your application (Use Facebook Messenger instead!)
* You **are not** handling sensitive user information that you don’t want passed through API.Ai servers. (You can most likely get around this with clever development and a well-written disclaimer)

## When not use
You probably don’t want to use API.Ai if:

* You **are** handling sensitive user information that you don’t want passed through API.Ai servers
* You answer to a big corporate team who need all data hosted on their own servers and want to minimise any external exposure/usage of that data
* You want a big enterprise solution




