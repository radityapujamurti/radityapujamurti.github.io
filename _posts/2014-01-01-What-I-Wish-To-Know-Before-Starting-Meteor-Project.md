---
layout: post
title: What I Wish to Know Before Starting a Meteor Project
tags: web_dev
cover: 
excerpt: Exploring MeteorJS as a beginner in web development.

---

Alright these things might be really obvious but if you are extremely excited to start your first project and want to jump straight to coding like me, probably you will miss these things too! Or maybe you have seen these things somewhere but they are not obvious enough for beginners like us. So these are the things that I miss when I first started my Meteor project.

### 1. You don't have to include JS, CSS, ... files explicitly.

If you have experience coding in other framework such as .NET MVC, you might be accustomed to include necessary files such as:
```js
rel="stylesheet" href="~/style.css"
script src="~/script.js"
src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.0/jquery.min.js"
```
    
However, Meteor is where magic happens! 
You do not have to explicitly include those files. Meteor automatically includes the files that you put in the project folder, alphabetically. Thus, if you want to make certain files to be loaded before others, you can rename them accordingly. You can find out more in this similar post on how to restructure your files.

### 2. Dynamic rendering with Blaze

Beginner like me never encounter such awesome thing like Blaze before. You can render template (something like partial view, if you are familiar with .NET MVC) or even toggle class reactively. Reactive simply means it will update the content without refreshing the page. You can harness this power using something like:
```js
{% raw %}
{{#if currentUser}}
//display something only users can see
{{else}}
//display something else
{{/if}}
{% endraw %}
```

You can do a lot more exciting things with Blaze, one of them is shown in this post. Some people might prefer React.js or Angular.js to be used with Meteor. This is hotly discussed issue at the moment. Personally I feel both of them have plus and minus, so depends on context. However, I will not delve further into the discussion here.

> However, Meteor is where magic happens! 

### 3. Packages
I think most people would agree that the existance of numerous awesome packages for Meteor helped them tremendously in their projects. There are so many packages out there and our job is to find the one we need. I personally love accounts-ui, Iron Router and Meteor Toys. You can Google it and find so many hidden gems that can save a big chunk of your project's development time.
In addition, we need to update Meteor packages frequently. I had one experience where the login button disappeared. After searching for the bug, a simple meteor update in command line fixed the problem.

### 4. Security
By default Meteor project is not configured with the most secure settings. We have to manually remove several packages such as auto-publish and insecure. You can read tons of useful articles to learn how to make your Meteor project more secure. Fortunately, Meteor has a well documented tutorial and this guide to achieve exactly this.

