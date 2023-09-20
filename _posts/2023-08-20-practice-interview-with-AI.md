---
layout: post
title: Practice Interview With AI
tags: AI
cover: 
excerpt: I created another app to help me prepare for future job interviews.
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/nePWYKWgtGc?si=oJgrqc5FZ_wk_5Y8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Main Features
This app shares similar features with the [German practice app]({% post_url 2023-07-29-creating-german-conversation-app %}) but there are some differences:
- Automatically ask questions related to a certain topic, instead of waiting for user input.
- Give feedback to answers (correct, partially correct, false), depending on the answer's score.
- Produce log records for past interactions to keep track of the scores.

## Problem

Job interview can be daunting. What we have prepared for months can evaporate due to nervousness when we are sitting across interviewers. Mock interview practice can help, but it is often expensive. As usual, I wanted to find a more cost effective, albeit not necessarily a better way to practice for future interviews 💰. 

## Solution

I reuse my German practice app that I described in [this article]({% post_url 2023-07-29-creating-german-conversation-app %}) as I do not want to reinvent the wheel. After some modifications, the final product is shown in the video above.

The main difference here is that the bot will take the first turn and ask me questions about a particular topic. In the video, the topic is data science. The bot will process my answer and assign a score. Based on the score, it will give corresponding feedback. For example, my first answer in the video received high score as it is close to the expected answer. The second answer I got it wrong. That is because I wanted to show bad answer and definitely not because I forgot the correct answer (just kidding, I totally forgot). The bot could successfully detect the answer is not complete and gave feedback accordingly. 

The app will also keep track of the scores to my answers. This is useful to see which questions I have problems answering. Then I can focus on learning those concepts. Unlike the German practice app, the bot will take some time to respond. This is because the answers to the questions are longer. It takes more time for the speech recognition library to translate it to text. However, this is just a minor limitation.

Cheers!