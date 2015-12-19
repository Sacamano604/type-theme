---
layout: post
title: Learning AngularJS - Day 3
---

I learned about arrays and filters so I jumped back to the first project I was working on to give it some tweaks. I learned about <a href="https://docs.angularjs.org/api/ng/directive/ngInit" target="_blank">ng-init</a>, which is used to alias special properties to <span style="color: #ff0000;">ng-repeat</span>, essentially a loop. What I would need to do in order to make <span style="color: #ff0000;">ng-repeat</span> work, is enter an array into the <span style="color: #ff0000;">ng-init</span> directive. Since we're on the theme of the World Cup, I went ahead and punched some football teams into an array and called it inside the container div I had placed already.

<script src="https://gist.github.com/Sacamano604/fdc3bc9211b56e711312.js"></script>I had my array in place, 6 teams. You can see that before I declare the elements I gave the array the name of ‘teams’. In order to call these ‘teams’ I would need to use the <span style="color: #ff0000;">ng-repeat</span> directive. I added the following.<script src="https://gist.github.com/Sacamano604/ee793b110ff55355e5c5.js"></script>

I use <span style="color: #ff0000;">ng-repeat</span> to show the individual ‘team’ in the ‘teams’ array. You'll also notice that at no point do I declare ‘team’ before I call it. From what I can understand, AnglarJS can declare and call this at the same time. So the logic for this unordered list is to repeat list items with a ‘team’ element from the ‘teams’ array.

I had a list. It was outputting the array and the teams were in place. However it was outputting them in the order that I had entered. To fix this, I found out about the filter ‘<span style="color: #ff0000;">orderBy</span>’. Because I was working with an array that was essentially a string of data, I couldn’t order by anything in the string...it would just display in the order of the array elements that I had entered them in. What I wanted to do was sort the teams in alphabetical order. After a long look around, you need to order by what’s called ‘<span style="color: #ff0000;">toString()</span>’. toString() is an AngularJS method that, from what I can tell, will sort a stringed array. It worked, my list was outputting in alphabetical order.

<script src="https://gist.github.com/Sacamano604/275d7217b09fd6e08b0c.js"></script>What I wanted to do from here was incorporate the text input we had in previous days, and use <i>it</i> as a filter. So that, in real time, the list would sort based on what was keyed into the input field. I punched in the input again, and gave it a new <span style="color: #ff0000;">ng-model</span> of ‘teamFilter’. Which made sense, I was using the input to filter teams.<script src="https://gist.github.com/Sacamano604/06e368c01dbd43f122f8.js"></script>

From there I had to edit the <span style="color: #ff0000;">ng-repeat</span> directive in order to receive the filter from the input. So along with the order I put in the filter.

<script src="https://gist.github.com/Sacamano604/e0283d8da1a24c43c478.js"></script>You see here, we want to repeat each ‘team’ in the array of ‘teams’, but filter by what’s being input and at the same time order it alphabetically. All the code looked like this, and it was working perfectly:<script src="https://gist.github.com/Sacamano604/6cc26b4074567c541707.js"></script>

I wanted to take it a step further by having more details per team so I went ahead and added in the stadium and city they play in. To separate elements i had to make sure they were in and object. Like so:

<script src="https://gist.github.com/Sacamano604/8e2e570d4d61a5d722ef.js"></script>That is one array element. It has a team name, stadium and city. I added these to all the teams I had in the array and it ended up looking like this:<script src="https://gist.github.com/Sacamano604/e076cdd2af6292d5ba29.js"></script>

Perfect, my array had more details than just straight team names. From there it was actually pretty easy to take it to the next level. This is what my list item code ended up looking like.

<script src="https://gist.github.com/Sacamano604/230dbd5da1eecf62978a.js"></script>

Let me explain the above code. We're calling for the <span style="color: #ff0000;">ng-repeat</span> directive to give us all ‘team’ elements in the ‘teams’ array, then filter by the input that’s entered, and sort by the ‘teamName’. This order could be sorted by city or stadium too. In this case I'm sorting by the team name. Then to display the elements I'm using the same ‘team’ call, but I want each of the ‘team’ elements: name, stadium, and city.

It was working perfectly. There is a way to link these externally through JSON and that is what I will be doing tomorrow. I will work on increasing the array to give us more elements to work with also.

<strong> Source Files:</strong> <a href="https://github.com/Sacamano604/Learning-AngularJS/tree/9ee299139dcacd4768c8e0ea0be2c867e080c83f" target="_blank">https://github.com/Sacamano604/Learning-AngularJS/tree/9ee299139dcacd4768c8e0ea0be2c867e080c83f</a><br />
<strong>Working Application:</strong> <a href="http://bentoussi.com/angularjs/day03/" target="_blank">http://bentoussi.com/angularjs/day03/</a>
