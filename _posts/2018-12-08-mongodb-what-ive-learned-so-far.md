---
layout: post
title: MongoDB - What I’ve learned so far
tags: database
cover: 
excerpt: In this post, I will share my impression on MongoDB in production environment for the past one year.
---

## Fine tune and optimize
Similar to other databases, the default setting for MongoDB installation is most likely not suitable for production.

The first document that we have to pay attention is MongoDB’s production note. Apart from the official documentation, there are other resources which can help us to further optimize MongoDB performance.

Make sure we understand each of the configuration item so we can tweak the values to suit our needs. Enable/disable journaling, how frequent is each checkpoint, how large is the oplog and WiredTiger cache, which compression method to use, do we need to enable profiling? Those are small example of configurations that can affect MongoDB performance in production.

Think of it as tuning a car; if you want to go off-road, you need a specific tire type. Similarly, each setting may vary, depending on many variables such as what OS you are running on, is it a dedicated mongod/mongos server, as well as your business requirement.

Once all settings are optimized, MongoDB performs like a champ!

## Choose the right version
Previously I thought the newest version is the best, so ALWAYS choose the latest version!!!

![](https://media3.giphy.com/media/3og0INyCmHlNylks9O/giphy.gif?cid=790b761174f28c02f4a10a7c2a25acd693ac733d0c1687a7&rid=giphy.gif&ct=g)

If someone asked me which version he/she should use today, I will opt for one version before the newest stable release with the latest minor release. For example, the current stable release is version 4.0. In this case, I will recommend using version 3.6, more specifically the latest minor release: 3.6.9.

Why? Because in early stage of stable release, there will still be sharp edges/bugs, most of the time. In each minor release, those bugs will be fixed so we want to avoid as many bugs as possible. The ultimate goal here is to have the most stable MongoDB version for our production environment.

However, this is not applicable to all cases. If you need multi document consistency a.k.a transaction in SQL out of the box, then you may need to choose 4.0 (you can still use older version and mimic the transaction on application level).

Similar to previous section, the key idea here is to know our needs and choose the version that can fulfill those needs. Check out the [release notes](https://docs.mongodb.com/manual/release-notes/) to find out what each version can offer! Reading the release notes is also useful to find known bugs and assess whether your system needs version upgrade.

## Storage engine matters
In official MongoDB, there are 2 main storage engines that we can choose: MMAPv1 or WiredTiger. I will not compare them here as there are many articles out there that feature in-depth comparison.

I have worked with both and today, I would recommend using WiredTiger but NOT when it is less mature.

When WiredTiger first came out, on paper it looks like a clear winner between the two. It has data compression, document level locking and other cool stuff! However, as this [article](https://clevertap.com/blog/sleepless-nights-with-mongodb-wiredtiger-and-our-return-to-mmapv1/) explained in great details, there were some performance issues in early stage of WiredTiger that forced the author of the article to return to MMAPv1.

The main lesson learn here is similar to the previous section: it is better to wait for a few months until a more stable version is released. If there is no urgent need to use the newest storage engine, be content with what we have.

In case you really believe that the new storage engine is totally better than the current one, use it in only in one of the replica set member. Make it the new primary and monitor for a few weeks/months before switching all replica set members to use the new storage engine. If it fails, it is easy to step down and choose a new primary that use the old and tested storage engine. That is also another strength of MongoDB, it is possible to mix the storage engine choice even within the same replica set.

## Official monitoring tool is excellent!

I have worked with MySQL and MSSQL briefly. I am really thankful that MongoDB provides an awesome monitoring tool, out-of-the-box. Refer to this [article](https://docs.cloudmanager.mongodb.com/tutorial/nav/install-monitoring-agent/) for installation steps.

A good monitoring tool is especially important for DBAs and other team members to monitor hundreds or even thousands of DB servers. MongoDB’s official monitoring tool is easy to install, has intuitive user interface and most importantly, able to send email or SMS alert for free.

The free version may not be enough for some and that is when the paid version comes to the rescue. Alternatively, we can build our own supplementary monitoring tool e.g. with ELK stack.

Those are the main points that I have learned so far. MongoDB is relatively young database and I believe there will still be a lot of improvement in the future.

Cheers!

