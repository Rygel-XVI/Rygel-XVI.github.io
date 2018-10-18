---
layout: post
title:      "Implementing a JS Front-end"
date:       2018-10-18 03:07:11 +0000
permalink:  implementing_a_js_front-end
---


When creating my Rails capstone I was so enthralled by the backend and loved what I made that I didn't give a ton of thought to the front-end design. I was not even sure how a front-end worked nontheless how it functioned with a back-end. Now I have a much better idea!

My app is a library app so on my list of books I realized it would be much cleaner from the user's perspective to add a dynamic create form that that only shows up in certain situations. When a book is created it also appends the Javascript object to the bottom of the currently shown filtered list if appropriate. Then you can re-open and clear the form to create yet another book without reloading the page making that whole process much smoother.

Another thing I was excited to implement was the index page of authors. It now loads the page from the front-end  and appends buttons to show a list of books the author has in the library. In addtion, each book that is shown has the option of showing a description and clicking on the title of the book to take you to the full show page of that book which includes more information and an option to checkout if it is available.

I was able to put a lot of functionality and information on a page in a dynamic manner that was easy for the user to find all without loading the page which would have wasted precious seconds.
