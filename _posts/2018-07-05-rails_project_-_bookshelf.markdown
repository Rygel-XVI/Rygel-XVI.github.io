---
layout: post
title:      "Rails Project - Bookshelf"
date:       2018-07-06 00:36:23 +0000
permalink:  rails_project_-_bookshelf
---


Falling off the coding wagon is bad but sometimes life happens and the combination of a big shift change at work, your partners employer suddenly going  a little crazy, and planning a wedding makes things a little difficult to get done. This didn't even include the family drama that occurred. However, it made completing my Rails project a bit more of an adventure.

By the time I got back to coding about a month later I realized I had forgotten more or less everything. I forgot how to customize routes, I forgot how to make a link, I forgot that validations existed (yep that happened), and I forgot how to use collection_select which I had down before I fell off the wagon. However, I still had the vision of what I wanted to make. A library app for my partner's classroom.  Over the years she has acquired quite a library for her kids and by the middle of the year it becomes quite an adventure to figure out where they have wandered off to.

So is the origins of Bookshelf. It has admin privilages which allow you to modify more or less anything in the program including other users info, filters, and the beginnings of reader statistics. But thereis so much more to add and do. For example, I want to create a scraper for the accelerated reader website so that instead of creating each book object by hand, it can be automated but that is probably a little down the line. I also discovered that a lot of the tweaking I want to do is really better done with javascript, so I am doing that in hard-mode for now.

I think the biggest challenge for me was implementing Omniauth with bcrypt especially since I wanted users to have to type in their password to change their data so I had to figure out a before_validation: system where it sets and handles the password differently until it is changed by an admin.  This project will probably never be fully finished as everytime I smooth out most of the bugs I start adding a new feature which then creates more bugs. 

However, it is a lot of fun. I think the most important thing when learning is to always challenge yourself. If it is easy then you aren't growing. The second most important thing is don't fall off the bandwagon.
