---
layout: post
title: Display Learning Metrics On Power BI
tags: data_science
cover: 
excerpt: A dashboard can help to improve learning by highlighting important metrics. 
---

![power bi dashboard](/images/blog/dashboard/interview.jpeg)

## Main Features
- Show usage charts on certain time period.
- Show aggregated scores e.g. average or minimum score.
- Identify a topic that needs the most improvement.

## Problem

I want to know which data science topic I should focus reviewing on. It is also good to see the progress I made along the way. 

## Solution
A dashboard can be a suitable solution for the problems above. There are many ways to build a dashboard. In this case, I chose Power BI because it is free and powerful enough for my use case.

The [interview practice app]({% post_url 2023-08-20-practice-interview-with-AI %}) has logging feature that keeps track of my answer's score in a CSV file. So I use the CSV file as a data source to Power BI. Creating various charts on Power BI is a pleasant process as there are many built-in options available. As long as the log is nicely formatted and contains all necessary data, charts can be created quickly. 

Another cool feature for Power BI is the possibility to design the dashboard. I modified the default style into a more minimalistic, but not so boring design. There are numerous ways the look and feel can be adjusted to our needs.

Creating trend lines (dotted lines on the line charts) can be useful to see the overall trend of certain metrics. For example, the line chart on top left shows how many questions answered for each day. The trend line has negative gradient which means there is decreasing trend on the number of questions answered. Hopefully, by looking at the declining trend, we are more motivated to practice more questions 😁   

One of the more challenging metric to calculate is to find the worst performing topic. This is shown in the orange card on the top right of the dashboard. It is obtained by looking at the average score for all question IDs (qid) in the past, finding qid with the lowest score then getting the topic for that qid. For the example above, 'gradient descent' is the topic with the lowest score. This means we need to focus on learning about that particular topic to improve the overall score. 

Cheers!