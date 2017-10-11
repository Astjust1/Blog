---
layout: post
title: "My Personal Site"
blog: dev
date: 2017-05-17
categories: jekyll webDev
show: true
---

# How? #
I chose [Jekyll](http://jekyllrb.com) as the static site generator for this site. Mainly because of the ease of use, but also because of the short learning curve. Getting set up was ridiculously easy. The hardest part of the whole project was modifying the CSS of the Material Design theme that I used. After making that decision, I needed to find a hosting service. I decided on Firebase because of the ease of customization/use and the extensibility. It would be very easy to add new features straight from the Firebase console. 

As I was deploying to Firebase for the third time while making changes, I began to get annoyed with how many steps I had to walk through to make the changes live. So after a bit of research I stumbled upon [TravisCI](http://travis-ci.org). Let me just say, that as a lazy person, continuous integration is a godsend. With just one .yml file I was able to automate the process of updating the website and redeploying.

## Next Steps. ##
Im currently working on a Blog editor web app. I want to be able to edit files, and create new blog posts on the fly. Im aware that tools like [Prose.io](http://Prose.io) exist, but I want to challenge myself to build my own and learn something new in the process. So instead of sticking with [ExpressJS](http://expressjs.com) as the base framework, I have decided to work with [SailsJS](http://sailsjs.com) to try and get everything working.
