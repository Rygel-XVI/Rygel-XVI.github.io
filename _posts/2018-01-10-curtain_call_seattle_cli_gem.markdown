---
layout: post
title:      "Curtain Call Seattle CLI Gem"
date:       2018-01-10 05:06:15 +0000
permalink:  curtain_call_seattle_cli_gem
---


I love theater. I grew up on Sondheim, Schwartz, and the VHS version of Pirates of Penzance. That is why it unsurprising that I am still an avid consumer of theater, especially musical theater. The Seattle scene contains numerous theaters. We have the 5th Avenue Theater and the Paramount which get the majority of the travelling Broadway shows. We also have a many of smaller theaters that are excellent, this includes a Children’s Theater, and the ACT Theater to list a couple. However, there are many theaters and no convenient way to see the shows playing at all the venues. So, I decided to create a gem to scrape and organize the shows to make it more convenient to figure out what is playing in the area.

 

I decided to start with the 5th Avenue Theater and Seattle Children’s Theater (SCT) as I frequent those often. The 5th wasn’t too difficult to scrape but SCT was difficult and will probably break a lot in the future. Not only did I discover that a ‘-‘ is not always a dash (there many versions of ‘-‘ that are actually special characters) but the SCT website does not use unique classes or id’s when the website was made so each time I thought I had found my selector it would undoubtedly go to a random spot in the page. I ended up having to ctrl-f through the source code to figure out what I was actually selecting. In addition to difficult selectors the page that has the list of shows and descriptions are named differently every season. So the 2016-2017 season will have that in the url. In an attempt to prevent it from breaking next season I had to drill down from the main page to get the proper url. However, The 5th Avenue had a conveniently named current season page named as such (yeay abstract page naming!) This has definitely taught me the importance of wrappers and unique classes and id's.

 

After finishing up my scraping adventure (and it *was* an adventure) I ran into my second most difficult challenge figuring out how to display the shows. Did I want a long list? How is the user going to navigate through the menus? How would a user want to interact with the shows and look at the data? After playing around a bit I realized that though some ways work now, in the future, if I expand the number of theaters I was going to run into the issue of too much information on one page. So I refactored the gem to make it so the user has to choose the show they want to see details of. This still has a lot of work and will be redone many more times...and then a few more times after that.

 

Overall, I am satisfied with what I have done. I think there are lots of improvements to be made over time especially with the date ranges and handling  user input of dates. Maybe I will eventually create my own Date class that has its own shows to help smooth that out or maybe I won’t have too. But displaying the information will without a doubt continue to be a challenge as the amount of data Curtain Call Seattle increases.


Check it out  https://github.com/Rygel-XVI/curtain-call-seattle-cli-gem
