---
layout: post
title:      "Sinatra Project - My Movie Library"
date:       2018-03-11 22:26:14 +0000
permalink:  sinatra_project_-_my_movie_library
---



Sinatra was my first exposure to working with a framework. Compared to my CLI Gem it was harder to figure out what to make. I am not a listmaker but realized that when my partner and I have friends over we often forget which dvds we have or can't find one that we were convinced we owned. So I thought it would be useful to create a simple app that allows you to create movies and associate them with genres. This way we won’t forget about a movie and we could sort them by genre so we won’t end up looking at detective movies when really we want a musical. One thing that I felt was important when I made it was for the user to create and manage their own genres. I debating setting up the generic genres, like action and romance, and not allowing the user to manage them but  in reality everyone categorizes things differently. I know when I am deciding on a movie or show or even episode to watch I don't think about if it's a romantic comedy I think about if I want a movie that has dogs, or feels 'edgy', or is nostalgic.  I wanted everyone to be able to make that decision themselves since it is unique to each person.
 
Making a Sinatra project from scratch wrote itself. The framework makes it easy to figure out how all the pieces fit together and often I found myself reusing code from each of the controllers and views. The hardest part was by far figuring out the best way of setting up the relationships. I actually had to go back and rebuild the database when I was close to done deciding to change the associations since I realized it was too complicated. I needed to simplify. Luckily, it wasn't too difficult to change it so that I wouldn't create Cthulu in Sinatra form.

One of the bigger challenges for me was thinking about what data to display and how to display it in a way that makes sense. When I made the CLI it was easy. I just had to decide what data I wanted and was able to go get it and to display it it would be a simple list. With Sinatra, it was more about creating good routes and really thinking through how a user would use the website. Where would it make sense to check that the user is who they say they are? When does it make sense to redirect to the index and how should I layout the links?
 
It also made me recognize all of the things I don’t know. How often is a database reset or purged? Is the application secure enough? Should i make some of the data created by one user accessible to others? There are a lot of things to think about with just the model relationships depending on how they will be used and that doesn’t even graze the fact that I am profoundly rusty at html and css. I look forward to integrating my knowledge more in the future and maybe expanding this project to something bigger and better (and more aesthetically pleasing) in the future.
