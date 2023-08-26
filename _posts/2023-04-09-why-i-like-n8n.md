---
layout: post
title: Why I Really Like A Low Code Automation Tool Called n8n 
tags: others
cover:
excerpt: It is an open source alternative to automation tools such as Zapier or Make. Being a low code tool, it allows flexibility for more complex workflows using Javascript. 
---

It has been almost a year since I started using [n8n](https://n8n.io/) in my job and it is safe to say I really like it.

The interface is easy to use and there are many template workflows available. For example, below is an [example workflow](https://n8n.io/workflows/1862-openai-gpt-3-company-enrichment-from-website-content/) provided by n8n. Let's see if you can guess the main idea behind this workflow just by looking at the image.

![sample workflow](/images/blog/n8n_intro/sample-workflow.png)

As you might guess, the workflow is essentially used to update Google Sheet information using data from certain HTML content/website. More specifically, the workflow will enrich company information on Google Sheet using information from company website that is analyzed by OpenAI's GPT model.

Using descriptive node names will make the workflow easier to understand hence anyone who sees the workflow for the first time will be able to understand it. We can easily see how the data travels from one node to another.

Being an open source software allows us to self-host and modify it if necessary. There is also n8n cloud offering for users who want to avoid the hassle of setting it up.

My favorite feature is custom code execution as shown below. 

![sample workflow](/images/blog/n8n_intro/code.png)

We can use Javascript to create custom logic in our workflow. This means n8n is suitable even for more complex workflows.

Thanks to n8n team and contributors for this superb tool! 👏