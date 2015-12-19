---
layout: post
title: Learning AngularJS - Day 11
---


This will be the last post in the ‘Learning AngularJS’ series. I will continue to create apps in Angular and blog about them but I would like to think I’ve progressed beyond the ‘learning’ phase to at least beginner.

The app was done in my eyes so I did some testing to make sure every facet of this project worked. After a little while I found a bug. When I added a team without an image file attached it wouldn’t add the team at all. This bug was something that actually worked in my favor since I didn’t really like having teams without an image.

To fix this issue I made the submit button disabled until there was an image put into the upload input. On the <span style="color: #ff0000;">addTeam.html</span> I gave the image submit input an <span style="color: #ff0000;">ng-model</span>:

<script src="https://gist.github.com/Sacamano604/ef681b2b08e94969ad5d.js"></script>

And used the directive <span style="color: #ff0000;">ng-disabled</span>:

<script src="https://gist.github.com/Sacamano604/dc0ae7e97d0f37f362e0.js"></script>

What this does it make my submit button disabled until there’s something in the file input.

I really enjoyed learning about AngularJS, and specifically I liked working on this project. However, part of me wishes I chose something a little more simple to learn some aspects of the language on but I learned so much in a small amount of time and I got to the end of the project anyways ;). I know it’s not perfect but it’s my first and I’d love to revisit this after a few months of AngularJS and see what I can do differently.

AngularJS is very powerful, and I'm looking forward to continue working with it.

<strong>Final Source Code:</strong> <a href="http://goo.gl/GGctM9" target="_blank">http://goo.gl/GGctM9</a><br />
<strong>Final Working Project:</strong> <a href="http://goo.gl/EpjZkz" target="_blank">http://goo.gl/EpjZkz</a>