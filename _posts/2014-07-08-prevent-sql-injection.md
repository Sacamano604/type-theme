---
layout: post
title: Preventing SQL Injection
---

As part of my ongoing AngularJS series I used PHP to insert/select to/from a selected database table. While building the PHP file I wrote the simplest code I could in order to achieve the task at hand. Unfortunately this code was riddled with holes and I was susceptible to something called <a href="http://en.wikipedia.org/wiki/SQL_injection" target="_blank">SQL Injection</a>. Without proper safeguards, my table becomes vulnerable to various forms of security attacks. Using SQL Injection, a hacker and pass a string input with the hope of gaining unauthorized access to a database. This is obviously something we don’t want happening.

What I needed to do was change my code so I wasn’t passing variables or actual values through the SQL query. This is the code that I had been using on my teams.php file.

<script src="https://gist.github.com/Sacamano604/02f9a3c7993c679a6d8b.js"></script><!--more--> In my switch’s list case, on lines 13/14 that I’m just openly querying the database. In the detail case, you’ll see on line 25-27 I’m passing a variable I assigned from the posted value of ‘ID’. And in the add case, I’m passing variables to my query again. All these are examples of bad php and mysql queries. Obviously this needed to be fixed. Along came <a href="http://www.php.net/manual/en/book.mysqli.php" target="_blank">mySQLi</a>, which is 'mySQL Improved Extension'. There are a few benefits to using mySQLi, the first being the most important.

<ul>
	<li>mySQLi gives you prepared statements.This is a safer way to send data to mySQL and protects you from SQL Injection.</li>
	<li>mySQLi enables most of the mySQL features.</li>
	<li>mySQLi is object oriented (which is really a benefit to me since I’m going down this path more and more).</li>
	<li>mySQLi supports transactions and multiple statements.</li>
	<li>The old mySQL is <a href="http://php.net/manual/en/intro.mysql.php" target="_blank">deprecated as of PHP 5.5.0</a> anyway.</li>
</ul>

So the choice was obvious. Let’s move over to mySQLi and not only will that be protecting me from SQL injection but it will also be a cool lesson to learn. First, we had to connect to the databse. From line 3 to 9 in the previous code snippet is how I connected to the database in mySQL. With mySQLi I could just pass it one but string.<script src="https://gist.github.com/Sacamano604/e37d2b19e2db5b5b42b0.js"></script>

Let’s go case by case in our switch and we can observe the changes I made.

<script src="https://gist.github.com/Sacamano604/08154de9b6ced8a82f4a.js"></script>Like before I was selecting everything from the table but notice under my $query I was using a prepared statement to access the database. From there I’m fetching the association of the row from the result. Not only that but the connection is only being opened when it needs to be and I close it immediately after the data’s been encoded to JSON.<script src="https://gist.github.com/Sacamano604/71549e07089e50a971d8.js"></script>

Just like the old PHP i was assigning the ‘GET” value of the ID to the variable <span style="color: #ff0000;">$id</span>. Then I use what’s called a prepared statement to setup the query. Notice how I have a question mark in place of the actual ID. What I do on the line below is bind the parameter to the integer of $id. In this case it’s an integer because it’s an auto incrementing key, but you could put in an ‘s’ for a string, a ‘d’ for a double, and a ‘b’ for a blob. From there I execute the query, ask it to give me the result back, and fetch the associated data to match the ID.

<script src="https://gist.github.com/Sacamano604/ca1f58b1d11d57ac321f.js"></script>

With the add case we started off the same way. We prepared a query, but notice the values we’re posting...question marks again. We’re binding the parameters to strings in the line under (9 to be exact) and assigning it to the posted value of each of the fields. From there we execute the query and close the connection.

<em>Keep in mind that you need PHP Version 5.4 or above for some mysqli features to work. I had to contact my hosting provider to make sure they supported it.</em>

I really enjoyed learning about mySQLi but more importantly it was nice to find a way to clean up my ‘hole-ridden’ code.