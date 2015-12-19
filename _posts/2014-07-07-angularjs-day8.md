---
layout: post
title: Learning AngularJS - Day 8
---

Before I get started I have to make sure to give a massive thanks to <a href="https://twitter.com/THEseanwalsh" target="_blank">Sean Walsh</a> on this section of the project. Not only did he help me understand some key components here but I was able to view first hand his thought process, his workflow and how he uses the <a href="https://developer.chrome.com/devtools/index" target="_blank">Chrome Developers Tools</a> to his advantage.

I had the list teams page, the details page, and the add teams page all in place. What I was missing was the uploading of an image to go with the team you add. Every club in the world has a badge (or logo) and I would like to be able to view this on the details page of the team. For this to work I had to make some major changes to the code I had in place, as well as learn about an AngularJS feature I had never used before: <a href="https://docs.angularjs.org/guide/directive" target="_blank">directives</a>.

<em>I should note now that I know for sure some of the code is not optimal, and the way I’m storing some of my data is not the best way. I would like to show the thought process I had and how I was able to achieve my end result. In my next post I will be tidying up my code and design. After that I will revisit this upload and clean up the way my php is handling the image.</em>

Under the line of code where I declare my <span style="color: #ff0000;">addTeam </span>function I created a new form data object and that's what I would use to pass the form data to the PHP file, from there I appended data that I would pull FROM the form fields.

<script src="https://gist.github.com/Sacamano604/ecaf07d32cd42f3fe195.js"></script>

Remember on <span style="color: #ff0000;">addTeam.html</span> how I gave every form field an <span style="color: #ff0000;">ng-model</span>? I would still use a model but I would have to change it to work with the above code. For example on the stadium field. Last post, I had this:

<script src="https://gist.github.com/Sacamano604/468e8e3bcdd5f56ea21b.js"></script>

Since we wouldn't be passing in a 'new team'anymore and just the data I changed it slightly to this:

<script src="https://gist.github.com/Sacamano604/98d2688190d97903aedd.js"></script>

Notice how the <span style="color: #ff0000;">ng-model</span> is just 'stadium'now. Essentially I'm appending the form data with specific field names and values collected from the input fields. So under 'stadium'grab the data from the <span style="color: #ff0000;">$scope</span> through <span style="color: #ff0000;">ng-model</span>.

For the next couple of steps I needed to do some research. I came accross a great article written by <a href="http://uncorkedstudios.com/blog/multipartformdata-file-upload-with-angularjs" target="_blank">Jenny Louthan</a> in which she has tackled this problem before and it helped me understand how angular handles multipart form data uploads. Our post request had to change also. Instead of passing a big chunk of data to the php file I had to be a little more specific. We were still posting, obviously, but also we would need to pass through the transform request and headers.

<script src="https://gist.github.com/Sacamano604/493fce8184d1bae511ac.js"></script>

We're still pushing the data off to the same PHP file, and we're still passing on the data but this time under the name of '<span style="color: #ff0000;">formData</span>' that you saw above. I needed to keep the data intact so I needed to add the transform request line you see. By default Angular will try and serialize the form data object so we need to override that. I set the content type to undefined because I want the browser to fill that in for me based on what's being sent to it. Then I'm redirecting the user back to the teams list after form submission is complete and successful.

Underneath my '<span style="color: #ff0000;">add</span>' controller I needed to insert a directive in order to grab the file from the form field. If you remember when I first discovered AngularJS I explained how it can teach HTML to do things. Directives are one way to accomplish this. So in a sense we're almost creating this directive to teach Angular how to deal with the file when it's been uploaded.

<script src="https://gist.github.com/Sacamano604/e333846055a5ab1a4f99.js"></script>

The above code is a directive that watches for any changes to the file upload input and pushes the selected file onto the <span style="color: #ff0000;">$scope</span>.

In order to execute I had to give my input tag our new '<span style="color: #ff0000;">fileread</span>' attribute. Alright. I was almost there but I had to know how the data was being sent to the php file. For that I used the Chrome dev tools. When the form was fully filled and submitted this is what angular was passing through: 
<br />
<a href="http://i.imgur.com/zV2bRm4.png"><img class="aligncenter" src="http://i.imgur.com/zV2bRm4.png" alt="" width="377" height="268" /></a> 
<br />
But when it got down to the image file, it's one massive base64 string. What I'm showing you below is just a small snippet. 
<br />
<a href="http://i.imgur.com/NOY2EmF.png"><img class="aligncenter" src="http://i.imgur.com/NOY2EmF.png" alt="" width="565" height="303" /></a> 
<br />
Now I'd sort of dealt with this before, on a hunch I went and changed the image column type in phpmyadmin to a <a href="http://dev.mysql.com/doc/refman/5.0/en/blob.html" target="_blank">blob</a> because I had remembered that they were able to hold large string data. My hunch was that if the browser is sending the data that way, could it do it in reverse. So I set the values of what's being posted to go straight into the database.

<script src="https://gist.github.com/Sacamano604/0d1e857cb7e29d9ece35.js"></script>

On my details page I added the following line of code to go along with my hunch:

<script src="https://gist.github.com/Sacamano604/63901146356151761bb4.js"></script>

Lo and behold it worked!! All I did was call the details through the scope like we did with all the other data. After hours of working with this image upload I was finally getting back the data I needed.

Here are the two first officially added teams with all the data.

<a href="http://bentoussi.com/angularjs/day08/#/teams/64" target="_blank">http://bentoussi.com/angularjs/day08/#/teams/64</a><br />
<a href="http://bentoussi.com/angularjs/day08/#/teams/56" target="_blank">http://bentoussi.com/angularjs/day08/#/teams/56</a>

Again, please remember that this is very untidy and needs clean up design wise and code wise. That's what I'll be doing next however I don't know if I'll post it as a full blog rather than maybe just a small update in case you're following along.

<strong>Source Files:</strong> <a href="http://goo.gl/EOQ6Rq" target="_blank">http://goo.gl/EOQ6Rq</a><br/>
<strong>Working Project:</strong> <a href="http://goo.gl/TvpeZC" target="_blank">http://goo.gl/TvpeZC</a>