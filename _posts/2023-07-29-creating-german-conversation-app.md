---
layout: post
title: Creating German Conversation App
tags: AI
cover: 
excerpt: I created an app to help me learn spoken German by simulating daily conversation.
---

<iframe src="https://www.youtube.com/embed/dvJnHjX9f4Q?si=J5sQBSVQ-oERBSve" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Main Features
- Capture voice input and reply with audio response quickly.
- Respond with the most appropriate answer, even though the input is not the same as expected.
- Provide translation to texts.
- Capture past answers to check any misunderstood answers by the automatic audio processing library.
- Provide hints for the expected answers.
- Responsive and interactive UI.

## Problem

I was looking for a way to practice speaking German without bothering anyone with my broken German 😁 After trying various apps including ChatGPT and Bing Chat, I could not find a tool that I am looking for. ChatGPT with voice input extension and Bing Chat have similar problem where they took rather long to respond. Waiting for a few seconds for a response makes the conversation less natural. In addition, they are multi-purpose AI models hence needs lots of prompting to start having conversation that I want.

There are good apps such as [Quazel](https://www.quazel.com/) that is close to what I wanted. It even provides feedback on the grammar and hints for a smoother conversation. However, the response time is not as fast as I desire. Like many other apps, it allows certain usage limit before asking us to upgrade to premium tier. I wanted to practice as much as I want with minimal cost so it seems I need to find a better way.

## Solution

So I decided to create a web app to solve these problems. The bot in this app does not need to respond to all kinds of question such as the meaning of life. It only needs to 'understand' and respond appropriately to what I say, even though my sentence has grammar mistake and not exactly the same as the given hint. I designed the app to give me response as fast as possible to make the conversation more natural. It also needs to provide translation to the hint and response.

As we can see in the video above, the bot responds almost instantly. To see how well the app captured my speech and review my pronunciation, there is a section to display past input on the right side. Even though I hesitated and used different words (as shown on the past input area), the app still understands me and provide the correct response.  The avatar photo will have ripple effect to mimic voice call, just to add a cherry on top.  

The app was built using Svelte and FastAPI. The text-to-speech (TTS) model is fast and able to produce realistic result, considering I generated them without using GPU. Thanks to [Thorsten](https://www.thorsten-voice.de/einfach-loslegen/) for the awesome TTS model!