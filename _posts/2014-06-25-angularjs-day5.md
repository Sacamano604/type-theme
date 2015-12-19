---
layout: post
title: Learning AngularJS - Day 5
---

It was time to build a back end. Rarely will you just receive static JSON files to display information, so I decided to throw the teams into a mySQL database, call the table, and parse it to JSON on the fly. This way if anyone wanted to add teams, they could.

Before I go any further I would really like to throw out a special thanks to <a href="https://twitter.com/THEseanwalsh" target="_blank">Sean Walsh</a> for helping me debug this part of the project and helping me understand some key components. I hit a wall a couple times and he was there to help guide me through the process.

Okay, so the first step I would need to take is to get the data to the mySQL table. I decided to work on my own server since I’d need to use HTTP requests with PHP and didn’t want to do it offline then move it online, so I worked exclusively online. In order to get my JSON file with the teams in it I needed to write some PHP. I created a table in ‘phpmyadmin’ with all the attributes, and even gave it an auto-increment ID. Then I created a quick script to decode the file and insert it into the table I had created.

<i>Please keep in mind for the PHP snippets I show I include a ‘&lt;?php’ on every snippet. This is only so that the syntax will highlight and color properly for you.</i>

I created variables for my hostname, username, password, and the database I was connecting to.

<script src="https://gist.github.com/Sacamano604/73cd88303162de16d6a0.js"></script>


Then I had to use the mysql_connect argument to pass the variables. In the line of code I had passed the connection string, and asked it to pass me an error if it failed.<script src="https://gist.github.com/Sacamano604/97dbbe6196ec9bedc762.js"></script>

Once connected, select the database or pass me an error.

<script src="https://gist.github.com/Sacamano604/e3b10b5946eb42e83d12.js"></script>Then I needed to get the json file and put it into a variable to be called upon.<script src="https://gist.github.com/Sacamano604/08cbf22a43b8a7d17b08.js"></script>

Once that was done I asked PHP to decode the JSON, and put that into a variable called ‘result’.

<script src="https://gist.github.com/Sacamano604/f628d3fe315f77293211.js"></script>Now came the part where I had to put the data into the table.<script src="https://gist.github.com/Sacamano604/d5bcc9ab717d75ebaf74.js"></script>

The code above is basically saying: for each result in the array, enter it into the table ‘teamList’ under the following headings...where the VALUES, from the JSON file, are as such. From there all I did was close the mySQL connection and echo to me that the parse was complete.

<script src="https://gist.github.com/Sacamano604/5022bf651c9a34b934c4.js"></script>I checked the table and all the data was pushed up. Excellent, I discarded the JSON file I was calling from, I didn’t need it. Our data was now on a mySQL database, and was ready for me to work with. Again, the idea here is to call the database and parse it to JSON on the fly for AngularJS to use. I created a file called ‘teams.php’ and I would start with the same first few lines, connecting to the database.<script src="https://gist.github.com/Sacamano604/ad0973cc100ae9b921b9.js"></script>

Then I would need to select everything from the ‘teamList’ table, as a query.

<script src="https://gist.github.com/Sacamano604/04d1b66a82ce68b277c8.js"></script>This next snippet of code was the tricky part. I’ll explain the code below.<script src="https://gist.github.com/Sacamano604/2133da41eb452efb7ae2.js"></script>

This is the first part where I really hit a wall. Instead of using ‘mysql_fetch_assoc’ I was using ’mysql_fetch_array’, which kept returning a value of null to me. Now, while it is an array I want, I am asking it to fetch me rows and I want the association for each column value. It took me a while to wrap my head around this concept. So in the first line I’m basically asking; if there’s a result from the query and while there are rows to pull from grab or fetch the row’s association. Then put it into an array named ‘$json’, for each row.

Now once I had that, I had to encode the data I had into JSON. I did that with this line:

<script src="https://gist.github.com/Sacamano604/835b725e44dc82a2faf0.js"></script>I ran ‘teams.php’ by itself and was getting a JSON array as an output. Perfect, almost there. Now I had to get angular to grab this file and parse it like it did with the straight JSON file. Because we had separated our files and put out controller in ‘footballApp.js’, that was the only place I needed to make a change in Angular. This was the line in our controller that I needed to change:<script src="https://gist.github.com/Sacamano604/a82d62d274d324a69f1c.js"></script>

Instead of grabbing the JSON file we needed to grab the JSON that the PHP file generated. So I made the following changes:

<script src="https://gist.github.com/Sacamano604/633a0b8e98712c576346.js"></script>

I was still using $http, but I needed to pass a couple parameters. What method to use, in this case GET, and the location of the file I need to ‘get’. It was working. I had my mySQL table being called by the PHP file, and parsed to JSON, then AngularJS was calling upon that and spitting it out into a table.

Here’s where I’m thinking this project should go next:
<ol>
	<li>Move the website link to it’s own column.</li>
	<li>Create ‘details’ pages so when you click on a team name you get extra details (may need to add more information to the database).</li>
	<li>Use the AngularJS ‘views’ to create that details page, and an ‘add teams’ page.</li>
	<li>Eventually an edit page too (?). If we do edit, we have to do delete also...it’s just the way it goes :)</li>
</ol>
<strong>Source Files:</strong> <a href="http://goo.gl/vZl52Y" target="_blank">http://goo.gl/vZl52Y</a><br />
<strong>Working Project:</strong> <a href="http://bentoussi.com/angularjs/day05/" target="_blank">http://bentoussi.com/angularjs/day05/</a>