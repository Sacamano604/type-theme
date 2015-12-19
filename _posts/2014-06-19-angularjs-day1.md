---
layout: post
title: Learning AngularJS - Day 1
---

AngularJS was something I saw all over the internet but was never 100% sure what it was . However I knew, at some point, I would have to learn this. It was all over the place and seemed to becoming an integral part of web development. I set out to learn and thought I would share.

AngularJS is what’s called a “SPA Framework”, single page application, instead of the traditional way where you would click something and the whole page would load or perform a task in full. AngularJS is supposed to take these to another level by introducing multiple views in one page. It is boasted as a full feature framework which allows you to data bind, has an MVC built in, validation, controllers and testing all out of the box. However, this is just a small portion of what the framework can do.

The first thing I did was head over to <a href="http://www.angularjs.org" target="_blank">AngularJS.org</a> and clicked download to get the AngularJS file (at the time I’m writing this the most recent version is 1.2.18). I went ahead and linked the file to a <a href="http://getbootstrap.com/getting-started/#template" target="_blank">bootstrap template</a> that I always start projects with.

<script src="https://gist.github.com/Sacamano604/8a745920e624e8c464d6.js"></script>Nothing special here, but I had included AngularJS into my page, which completed step one. It may look confusing but it’s actually a pretty basic template for a page, and I’ve commented it out for you to understand each component. At this point I learned about ‘directives’. Directives are a way to teach HTML new things. <span style="color: #ff0000;">ng-app</span> is the first directive that I learned about, which is a built in directive. It’s placed inside the HTML tag and lets AngularJS know that we need it. From there I learned about <span style="color: #ff0000;">ng-model</span> which puts whatever attribute we give it into what’s called <a href="https://docs.angularjs.org/api/ng/service/$rootScope" target="_blank">the scope</a> . From there you can add what’s called a data binding expression to it, which is indicated through curly brackets. I went ahead and added the app directive to the html tag:


<script src="https://gist.github.com/Sacamano604/4f4c91b1111eef9386a4.js"></script>

AngularJS has been called upon, but we still need to work with it. From there I applied the model directive to a text field and placed the div in between the body tags.

<script src="https://gist.github.com/Sacamano604/21d29fae19bd56bf392b.js"></script>Now as it stands it does nothing. AngularJS is present and called upon but it’s not required to do anything. Now, this is where the magic happens and to be honest it blew my mind. All I need to do to call upon the input to the text field is to enter: <span style="color: #ff0000;">{{ name }}</span> Name being whatever we apply to the ‘ng-model’ directive, in this case we called it ‘name’.<script src="https://gist.github.com/Sacamano604/e770f6573dc45f3e81f6.js"></script>

Now whatever is being typed into the input field will be copied, or echo’d or called upon…whatever you like to call it (don’t hesitate to comment with the correct terminology please).

Day 1 of AngularJS opened my mind completely. The simplicity required to complete the task I did was awesome. I can tell just after one day that this is a powerful framework and I will be continuing this series.

<strong>Source Files:</strong> <a href="https://github.com/Sacamano604/Learning-AngularJS/tree/fe445265767f5b97b4f409204b087f3eff2ccff8" target="_blank">https://github.com/Sacamano604/Learning-AngularJS/tree/fe445265767f5b97b4f409204b087f3eff2ccff8</a><br />
<strong>Working Application:</strong> <a href="http://bentoussi.com/angularjs/day01/" target="_blank">http://bentoussi.com/angularjs/day01/</a>
