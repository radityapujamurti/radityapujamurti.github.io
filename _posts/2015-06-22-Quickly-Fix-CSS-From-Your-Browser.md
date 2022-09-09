---
layout: post
title: Quickly Fix CSS From Your Browser
tags: web_dev
cover: 
excerpt: I did not know browsers can be this powerful!
---

This article is intended for those who are new to CSS

Configuring the CSS often can be tricky, especially when we take over project from someone else. Generally, we should know how CSS works in affecting how each element is rendered. There might be more than one CSS rule applied to the same element and you may ask, which rule affects the element? As a rule of thumb, CSS rule that is placed last is the one that affects the element, as the name suggests (cascading).

However, there is !important statement that prioritize the element with the !important statement to affect the element event though it is placed way on top of the file. This can be useful in the time where we want to make sure all elements conform to certain rules, such as font-weight and font-size. But please use it sparingly as it will result into a situation where almost all of your CSS rules have !important in it, which defeats the purpose of the statement in the first place.

In determining which CSS rule affects which element, I personally feel the easiest way is to use our browser. These are the steps you can do (I am using Chrome but you can use your favourite browser as well):

- Right click on the element that you want to examine and choose 'Inspect element'. This will open a window that shows you various CSS rules that are related to the element as shown by the image below.

![]({{ site.baseurl }}/images/blog/fix_css/1.png)

- You can do the modification directly to the CSS rules. The change will be reflected directly in the browser.

![]({{ site.baseurl }}/images/blog/fix_css/2.PNG)

For example, on the image above. You would like to modify the font size of h1. Click on the number 36px and you can edit the value accordingly. You can even use the arrow up and down on your keyboard to automatically increment/decrement the value. This is more efficient than having you switching back and forth between your project and browser then refresh to see the changes.

- Make the necessary changes to the CSS rule. After you are done, simply click and drag to select (you will see the rule is highlighted as you select them as shown in the image below) the rule that you want to copy then Ctrl+C to copy the code to your clipboard.

![]({{ site.baseurl }}/images/blog/fix_css/3.png)

In the image above it assumes that you add color and font-weight to h1. You can add a rule by clicking the area around the existing rule(refer to the image below).

![]({{ site.baseurl }}/images/blog/fix_css/4.png)

- The next step is to find the correct CSS rule that affects this element in the project. This is arguably the hardest part, especially if your project has complex CSS rules that overlap with one another. If you are lucky, the browser will tell you the CSS file that contains the rule (for the sample image above, you can see bootstrap.css which indicate the CSS rule is located there. Otherwise, you have to find it manually.

- After you find the corresponding rule in your project, you can paste the copied rule from the browser and you are done.
Refresh the page on your browser to ensure that all the changes are implemented properly.

One thing to take note here is that you have to remember what changes you make. Often we forget to copy and paste the CSS modification on browser to our project. When we refresh the page, all the changes are gone as the project file is not updated. What you can do is to edit the CSS rule on browser, copy paste the changes to the project then continue editing the CSS rule on browser. By splitting the updating of CSS rule to your project in several times, it is less likely you encounter the mistake of editing the CSS on browser only and forget to apply the changes in the project.

