---
layout: post
title: "Thoughts on Restrictive Frameworks"
blog: dev
date: 2017-05-23
categories: webDev express javaScript thoughts
show: true
---

# Why so restrictive?!?! #

It's possible that it's just me, but I don't really work well with being forced into a certain
way of thinking. I like the freedom to process and organize my code/thoughts how I best see
fit. Now that's not to say I'm perfect in the slightest, but I still enjoy that freedom.I plan to go into a bit of detail about the blog editor that I'm building for myself and the framework choices that went with that.

## Let's set sail. ##

I've been looking to invest my time in learning some new JavaScript frameworks, so for this project I decided to start out with [SailsJS](http://sailsjs.com). It was an interesting premise, promising to pave a path for rapid development by wrapping and extending express with a multitude of features.

- Built in ORM
- Built in Socket support
- Rails like controller/model generation..etc

I do have to say, that all in all, they definitely did deliver on their promise of rapid development, but much of the functionality and customization options were, at least in my opinion a bit convoluted. While, for instance I could see why the app.js was just an entry point for running the app outside of using

```sh
sails lift
```

it also stopped me from structuring things the way I would have wanted to. Which is why I went back to the minimalist approach and restarted with Express

## Express is my friend. ##

Most of my happiness with [ExpressJS](http://expressjs.com), stems from my familiarity with it,
but some of it also comes from the lack of hand holding that it provides. I was able to get a skeleton landing page up and running in about 15 minutes vs the hour it took trying to figure out Sails. I'm sure with some more experience in general, I could go back to sails with a new perspective and try to better understand some of the design decisions, but for now, Ill stick with my trusty buddy Express.