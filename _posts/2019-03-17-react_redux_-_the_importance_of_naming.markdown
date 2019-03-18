---
layout: post
title:      "React/Redux - The Importance of Naming"
date:       2019-03-18 03:12:07 +0000
permalink:  react_redux_-_the_importance_of_naming
---


So the front-end is messy. I think that's why I am more drawn to the back-end, it's just cleaner, more succinct with a little less 'magic'. One thing that I realized is that how it is organized is so much more important. Files are imported so if you need to change the name of one to have it make sense you then have to find every place you used it so you can change that name too. It's a scavenger hunt. However, as a newbie using React, figuring out exactly what containers and components you will need is impossible and inevitable this happens a *LOT*. I started out with a lot of files that were overly specific in their naming, like RecipeIngredientSearchContainer (talk about a mouthful), only to realize later that I should really just be called SearchContainer. The extra words and syllables created extra confusion for me, the developer, making it harder to figure out what goes where. 

<br>

I would look at my list of files and just felt confused. So I decided to separate my overly-wordy files and put them in folders that described what route they were related to. Everything relating to object creation or modification would go in this 'modify' folder and everything related to the search section would go in the 'search' folder. It sounded good at first glance but it didn't really help especially when I started importing files from 'search' folder to use in the 'modify' folder.

<br>

After much googling and much blog reading about file organization in React. I finally figured out that I needed a concise simple way to name all the components (keywords **concise** and **simple**) and just separate them into containers and presenational components like Flatiron showed us (imagine that). I saw some really interesting ways of organizing files in some Github Repos that were leagues more complicated that my little project but that is something to strive for a different day.

<br>

So in the end make sure your names make sense and that you can tell what they do with a quick glance. Use as few words to describe it as possible.  Make related files seem like they are part of that file 'path' (CreateContainer contains CreateRecipe and CreateIngredient for example) and everything becomes more clear. The saying is an organized desk equals an organized mind. I don't normally adhere to that (you should see my desk) however, if the pile is so large that you can't make heads or tails of it, that probably means it's time to reorganize!

<br>

Also, at some point, someone else will try to understand what you did...and so do you in a month.


