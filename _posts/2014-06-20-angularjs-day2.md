---
layout: post
title: Learning AngularJS - Day 2
---

Today, instead of starting something new, I decided to experiment and mess around with the simple data binding. I thought, if it can data bind on the fly like that...could it do math on the fly? I had a thought to create a temperature convertor with AngularJS from what I'd learned so far.

The idea would be to input the temperature into a text field in celsius, and have it output the temperature in fahrenheit (and vice versa).

<b>Celsius to Fahrenheit.</b> For this I changed the <span style="color: #ff0000;">ng-model</span> directive to something that would make sense for this calculation, so I called it ‘celToFar’. From there I went ahead and put the formula around it. So what I had was, <span style="color: #ff0000;">{{ ((celToFar * 9) / 5) + 32 }}</span>. I had it working, it was fine and outputting the correct temperature. However, before an input was even made I would get the following error “NaN”. Which from javascript, you know means “Not a number”. This is when I learned about<a href="https://docs.angularjs.org/api/ng/filter" target="_blank"> filters</a>. You can filter results to be numbers, dates, currency, uppercase, lowercase, etc. I went ahead and added the ‘number’ filer to my output and it worked perfectly. We were in business! Here’s what I had:

<script src="https://gist.github.com/Sacamano604/f12921497cb861d0349a.js"></script>The only problem here was that, by default, the app would just display ‘degrees fahrenheit’ without any input. My friend, <a href="https://twitter.com/THEseanwalsh" target="_blank">Sean Walsh</a>, suggested that I look into the <span style="color: #ff0000;">ng-show</span> directive. What I found out about ng-show was that whatever element you would add it to, would only show based on the conditions you give it being ‘true’ or ‘truey’. I decided to add it to the ‘p’ tag. And I would make it equal the ng-model directive I gave it.<script src="https://gist.github.com/Sacamano604/534e0c8c920b02035991.js"></script>

The only problem with this, is if the value entered into the input field was the number ‘0’...it would return false and not display the p tag. I fixed this with an OR statement but I should tell you at this point that it took me a while to figure this out, I don't know why but the theory didn't 'click' with me until I tried it in practice. Here’s what it all ended up looking like:

<script src="https://gist.github.com/Sacamano604/21d00b7b4283e479ad1d.js"></script><b>Fahrenheit to Celsius.</b> Because I had went through the steps and made all the mistakes this one was the easier part. I went ahead and added the formula, number filter, and the ng-show directive.<script src="https://gist.github.com/Sacamano604/8bc955578ed307e53ec4.js"></script>

I really enjoyed this exercise, it was a great ‘next step’ for data-binding and the exciting thing is that I’m just scratching the surface.

<strong>Source Files:</strong> <a href="https://github.com/Sacamano604/Learning-AngularJS/tree/38012d5fd7a592ede982f14c18d5191e4e5fb683" target="_blank">https://github.com/Sacamano604/Learning-AngularJS/tree/38012d5fd7a592ede982f14c18d5191e4e5fb683</a><br />
<strong>Working Application: </strong><a href="http://bentoussi.com/angularjs/day02/" target="_blank">http://bentoussi.com/angularjs/day02/</a>
