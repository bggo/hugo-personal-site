---
title: "Deploying a personal website"
date: 2020-08-18T17:12:21-03:00
draft: false
---

## Part 1 of 4 - Deciding the stack

>  After a long time without writing some tech stuff I have decided to put my website/blog back online! Writing here was a fun task to document the process itself. Hope you enjoy.

Back in time I used to host my own server, either in my home or in the early beginning as a IaaS Machine on the cloud, many times as a shared VPS or a tiny machine where I could have my Debian OS, with Apache as a webserver to run some PHP code using Wordpress.org framework. That does not require a lot of effort but, nowadays lots of things have changed.

I thought that after almost 8 years would be some way to do this kind of thing in a more straightforward way, and yes, there are many ways. I decided to pick tools that I could deal less with infrastructure and cloud services and I have picked some options to abstract all this work, but that still gave me a lot of flexibility. So this is what I choose:

[GOHUGO.io](https://gohugo.io) - This is a very lightweight framework to develop your site/blog, written in go, but so far I just needed to understand a little of toml, yaml and the classics of CSS, JS and HTML. Yep, it is way simpler than wordpress, but as a provocation, I never used like 10% of all the functionalities of wordpress. 

[Firebase Platform](http://firebase.google.com/) - I was really blind when I associate firebase as an old database or a new document store only database. I get some time to discover and run some codelabs to understand better the power of the firebase platform. As a part of GCP, Firebase platform is a full suite of tools to develop, host, analyse, integrate and other tons of cool stuff for your APPS web or mobile. Strongly suggest you read some about it. As I'll need to host the website, why not go PasS instead of IaaS.

[TravisCI](https://travis-ci.org/) TravisCI (https://travis-ci.org/) - And as I'm really up to automation, I have used travisCI to get all the code I pushed into github to a new deploy on firebase hosting, automagically. =D

So having said that, I'll be in the next articles documenting how this journey was. Stay tuned!

Ah..footnote: Zero Cost.

Read this article on [Medium](https://medium.com/@brunogurgel/deploying-a-personal-website-b32f06df123)
