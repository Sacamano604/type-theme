---
layout: post
title: AngularJS Services - Part 1
---


Most recently I completed <a href="https://twitter.com/gordon_zhu" target="_blank">Gordon Zhu’s</a> AngularJS course at <a href="http://www.angularcourse.com" target="_blank">angularcourse.com</a>. Before I go any further I have to say that this is one of the best tutorials I’ve seen out there for learning AngularJS. He outlines everything a beginner should know and then some, so if you’re new to the framework I’d recommend heading over there.

This course gave me some cool ideas about projects that I’d like to work on, but more importantly this course introduced me to <a href="https://docs.angularjs.org/guide/services" target="_blank">services</a>. While I’m eager to move on to other projects I thought I’d take my existing project and refactor the code. I was repeating myself a lot and thought it was important to make sure my app was as tidy as possible.

<em>Disclaimer: I changed the way I organized the file system with my app, so if you’re following along maybe double check my source code link to make sure you’re where I’m at.</em>

The first service I created was a service that would grab the list of teams. I’ll take you through it, step by step.


I created a file called <span style="color: #ff0000;">footballServices.js</span> and linked it to the <span style="color: #ff0000;">index.html</span> file like the rest of my js files. From there I made sure that my <span style="color: #ff0000;">footballApp.js</span> file knew that I needed my my service module. The top of my <span style="color: #ff0000;">footballApp.js</span> file looked like this:

<script src="https://gist.github.com/Sacamano604/ba435430347802afeeda.js"></script>

From there I had to create my <span style="color: #ff0000;">footballServices.js</span> file. First thing I did was declare the the module:

<script src="https://gist.github.com/Sacamano604/4fb517f62fbbf7c4484f.js"></script>

I had learned about two different ways to work with services (there are more but I only know about two at the moment). You can have a value or a factory. In the simplest possible terms a value service would represent a value, like a link location, or a single variable. And a factory could be a function. What I needed was a function because I needed the app to perform the function and return a value to me.

I called my factory ‘<span style="color: #ff0000;">teamListService</span>’ and asked it to pull in the <span style="color: #ff0000;">$http</span> dependency. From there I needed it to return a callback function that would grab the values from my php switch. This is what my service looked like:

<script src="https://gist.github.com/Sacamano604/fabc9ccf8aadb1f5a949.js"></script>

Now I had to move onto the controller itself. Because i didn’t need the <span style="color: #ff0000;">$http</span> dependency anymore, I removed that and added in the dependency for the <span style="color: #ff0000;">teamListService</span>.

<script src="https://gist.github.com/Sacamano604/a463a59ec35956681992.js"></script>

You can see the code is a lot cleaner here. Moving the get function to the service and moving my directives to their own file has already cleaned up my code. I still have a lot of repeating code however, and will continue to refactor and put functions into services.

The end goal here is to have the most perfect code I can, for what I have but as always feedback is appreciated.

<strong>Source Code:</strong> <a href="http://goo.gl/vbLfPG" target="_blank">http://goo.gl/vbLfPG</a><br />
<strong>Working Project:</strong> <a href="http://goo.gl/VuL2f8" target="_blank">http://goo.gl/VuL2f8</a>