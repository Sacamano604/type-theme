---
layout: post
title: Learning AngularJS - Day 9
---

It was time to create the page where you can edit teams. I needed to change a component of this project; how I was handling images. Entering the image as a base64 blob into the database was cool to see and was useful in getting the project moving along. However, it’s not going to be viable when I incorporate an edit page not to mention the logistics behind having the browser decode and encode base64  all the time (quite simply, it’s just way too slow).

As always, the first thing I did was point the controller view to the correct location:

<script src="https://gist.github.com/Sacamano604/c95d2c5a15f719f3393e.js"></script>

Then I created the edit team page itself with the form fields. 

<script src="https://gist.github.com/Sacamano604/1896e9f9741b904c3b41.js"></script>

Everything’s the same except the model, where I appended a ‘<span style="color: #ff0000;">teamedit</span>’ in front of it purely for continuity and organization. Now one thing to note here is how I handle teams with and without images in the database.

Take a look at line 44 to 50. What I’m doing is hiding the upload field <em>IF THERE’S AN IMAGE PRESENT</em>, and it will show the file name. This way we don’t have doubling on the upload and the user will know if the team has an image present already. Conversely, if there is <em>NOT</em> and image present show us the upload field.

The edit controller started off pretty simple. What I wanted to do was borrow the details switch in order to populate the form values on the page. If there’s data to show, show it as values in the form fields.

<script src="https://gist.github.com/Sacamano604/c917f71711605cda6583.js"></script>

This would also put the image filename into the scope so I could use it in cases where there was already an image present. From here I had to organize the form data passed to the php file in a way that it can take. We’ve done this before for add team so it wasn’t too difficult to get right.

<script src="https://gist.github.com/Sacamano604/b5927ba24be2fbc425d6.js"></script>

You’ve seen all this before but one thing to note are lines 12 to 15. That if else statement is handling which data gets passed to the php side through the ‘<span style="color: #ff0000;">image</span>’ variable.

If an image is being uploaded then use the following to append to the form data:

<script src="https://gist.github.com/Sacamano604/60876772a62d26983731.js"></script>

Otherwise use the file name:

<script src="https://gist.github.com/Sacamano604/89cca53a38a26ae495cf.js"></script>

Alright. The views were in order, the form was working and the controller was handling the data. All I needed to do was get the php to post the data to the database and I was good to go.

<script src="https://gist.github.com/Sacamano604/8a6f1247d1c98de99b33.js"></script>

I created an ‘<span style="color: #ff0000;">edit</span>’ case and assigned the ID we got from the URL, and the posted image to variables to use later. Then I created an if else statement to handle the two types of images that could be passed (the file name if an image exists, or the base64 data if a new one is uploaded).

<script src="https://gist.github.com/Sacamano604/e0bc9d0905aad7c14db0.js"></script>

The code above you’ve mostly seen before, except the first line. What I’m asking for here is if the image data string contains the string “<span style="color: #ff0000;">base64</span>” then go ahead and treat it like a base64 file like we’ve done in the past. Otherwise just treat it like a normal data string and pass the posted name to the <span style="color: #ff0000;">$file</span> variable.

From the <a href="http://www.bentoussi.com/preventing-sql-injection/">previous blog post</a>, I talked about SQL Injection so I needed to make sure we continued down that path. This is how I passed all the data to update the table row.

<script src="https://gist.github.com/Sacamano604/0cd081ad87977319c39f.js"></script>

We’re passing the image and id as variables that we assigned previously, and notice that I’m using the ID to match the row we need to update.

Working! Long path but we’re nearly there. All I need to do is create a controller to handle the deletion of the team/row.

<strong>Source Files:</strong> <a href="http://goo.gl/fuz3TZ" target="_blank">http://goo.gl/fuz3TZ</a><br />
<strong>Working Project:</strong> <a href="http://goo.gl/Ju70dQ" target="_blank">http://goo.gl/Ju70dQ</a>