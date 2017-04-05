---
layout: post
title:  "Working with sensitive data in API.Ai"
date:   2017-04-05 13:20:00 +1000
categories:
tags: [machine learning, chatbot, api.ai]
---

## Intro

If you have seen my [Api.Ai Chatbot AI Review](http://taylorbett.github.io) then you are aware that API.Ai introduces a problem for enterprise or other development environments where data security is paramount: you cannot host your own instance of your API.Ai agent.

This means that all user interaction with the Bot passes through the externally (to your application or company) hosted API.Ai servers that run your agent. If this is a problem for you, then you might consider IBM Watson as an alternative, **or** you might consider the following development practices for working with sensitive data in API.Ai.

## Please note:

Please note that the following practice **will only help circumvent data security issues on your own web application**. Using any integrations or other channels will still pass your data through the API.Ai platform, and as such this way of dealing with data is only really helpful if you don't plan on using API.Ai's other integrations.

The typical flow of user queries through API.Ai goes as follows:

![API AI data flow diagram](https://files.readme.io/a769bab-API-AI_key-concepts.png)
Source: [https://docs.api.ai/docs/key-concepts](https://docs.api.ai/docs/key-concepts)

You can see the problem here if you are using sensitive data in your user queries.

For example, if your customer wanted to access some details about their order, they would need to input some form of authentication or an order ID number through the chat interface.

## Solution

If you do not want to pass these sensitive details through the API.Ai platform, you will need to strip them out of the query before you send it to the AI platform, and reserve them for use in your own application, making any API calls directly from your application rather than through the API.Ai platform. You could potentially replace them with dummy details of similar format in the query to API.Ai in order to preserve the language structure of the query for the natural language processing (NLP) of API.Ai to handle.

Once you have stripped out any sensitive data, you pass the query to API.Ai as normal, in order to use the NLP capabilites of the bot to help you determine the user's intent. At this point, the AI agent will match the incoming query against your [intents](https://docs.api.ai/docs/concept-intents) as you have configured it to do.

However, rather than use your web hook to make an API call from the agent, you can return an [action](https://docs.api.ai/docs/concept-actions) (or other data as part of the reply from the bot) to your application, which you will catch and use to trigger your custom behaviour. This is where you would use the reserved sensitive data from the user query to make your relevant API call, all from the secure comfort of your own application, preserving data security. You can even perform this API call before you print out the AI agent's response, giving the impression of the bot doing the work.

This practice will allow you to utilise the NLP capability of API.Ai to determine user intent, and give the user a seamless natural language chat interface through which they can interact with your/their secure data and BED layer services.
