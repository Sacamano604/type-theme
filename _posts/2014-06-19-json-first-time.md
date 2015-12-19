---
layout: post
title: Working with JSON for the first time
---

While brainstorming ideas for projects in order to improve my Javascript skills one of the ideas I had was to make it some how involve the World Cup. It was coming up and I absolutely love football so why not incorporate it somehow. I hit a lot of walls on where to get started. Whether I should make it interactive, or static and update some sort of XML file myself. I wasn't exactly sure, and I couldn't settle on something so I preoccupied myself with other projects.

Until I had a friend of mine link to me a ‘World Cup in JSON’ project here: <a href="http://worldcup.sfg.io/" target="_blank">http://worldcup.sfg.io/</a>. I had always seen JSON here and there on the Internet but, to be honest, I found it very intimidating. Even so, I knew it would have to learn at some point and why not now, during the World Cup.

After reading I noticed that it’s not that much different from XML. I could work with this, it’s just a big array of data. So I set out to learn how to parse this data. I found <a href="http://json.org/" target="_blank">http://json.org/</a> and read there too. I was surprised at how many languages can parse this data. I saw that I could use PHP and since I was working with it earlier that day I decided to give it a go.

I didn't know how to access the JSON file or parse the data but after some searching online I found these lines of code that made it possible:

<script src="https://gist.github.com/Sacamano604/2f3de5e574afd0f26bbe.js"></script>I didn’t have ‘true’ in there for a while, but it needs to be to return objects into arrays. I learned the hard way but that’s the beauty of it too. From there I took a simple for each statement and tried to return a couple of the values. I just went with the first two “Country” and “Wins”. Put them in an unordered list for now, with the intention of displaying them as tables/groups eventually. So my whole code looked like this on the first test:

<script src="https://gist.github.com/Sacamano604/0d2d9f56c64c901181f8.js"></script>

Once I was able to access the data, I knew that I needed to organize them in groups because I was pulling the group results…doesn’t make sense for it to be one big list. So I added an if statement just to pull the country and wins from group 1:

<script src="https://gist.github.com/Sacamano604/501dd32357a46664c6e0.js" type="mce-text/javascript"></script>From here all I needed to do was make it into a table, group them up, and add the other columns. I ended up with this:<script src="https://gist.github.com/Sacamano604/21fa9ee84eedcb88bcfe.js"></script>

But with doing something like this it will end up being one long file of tables. At the end of the day I was able to get the result I needed but <strong><em>with certainty this it not the most efficient way to pull data from JSON, I can just tell by looking at it. I will revisit this in hopes to clean the code and make it more efficient but for day one JSON I think I did well.</em></strong>

<strong>Source Files:</strong> <a href="https://github.com/Sacamano604/JSON-Testing" target="_blank">https://github.com/Sacamano604/JSON-Testing</a><br />
<strong>Working Application:</strong> <a href="http://bentoussi.com/json/" target="_blank">http://bentoussi.com/json/</a>

<p><strong>Update Dec 12th, 2015: </strong> Looks like the API is not available anymore as my tables are showing up blank. But the code is still applicable. </p>