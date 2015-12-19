---
layout: post
title: Learning AngularJS - Day 7
---

The next step in the project called for a form to add teams to the table. At this point I was thinking of new columns to add so that the details page had a little more to it...I came up with image and details. Details being a paragraph or two about the team’s history (basically a small snippet from the team’s wikipedia’s page). <strong><em>The image column will need an uploader and some sort of verification so I will leave that for a blog post on it’s own.</em> </strong>Let me walk you through the changes I made to each of the files in our project.

We needed to create the ‘<span style="color: #ff0000;">addTeam.html</span>’ page. Very straight forward, but notice how I change how I present the form. Previously I would always display this as a table which is not scaleable, and definitely not ‘responsive design’. Instead of using table data, I used labels and bootstraps column divs. My form ended up looking like this:

<script src="https://gist.github.com/Sacamano604/4adc83142a4fd7637229.js"></script>

<!--more-->

Couple things to note here. First, the controller I declare is '<span style="color: #ff0000;">addTeamController</span>' which we have not seen before but I’ll be showing you how I added it to my controllers file. In the same tag I also declare an <a href="https://docs.angularjs.org/api/ng/directive/ngSubmit" target="_blank">ng-submit</a> of ‘<span style="color: #ff0000;">addTeam()</span>’...which is the function I used to pass along the form data. To collect that form data I’ve given every input an<span style="color: #ff0000;"> ng-model</span> of ‘<span style="color: #ff0000;">newTeam.[inputname]</span>’. You will see in the controller how this comes together, but essentially the model is collecting all the data for me and passing it through to the controller. Also know that the <span style="color: #ff0000;">ng-model</span> on the submit button is submit, and at the point of click collects all the model data for us. Now that I had a form to add teams I had to let the route provider know the new path. To the <span style="color: #ff0000;">footballApp.js</span> file I went ahead and added the following code.

<script src="https://gist.github.com/Sacamano604/eb17084435d58da67040.js"></script>

I pointed this path to the <span style="color: #ff0000;">addTeamController</span> so let me show you how I constructed that controller now. I started off with this:

<script src="https://gist.github.com/Sacamano604/e9917c3cee1800188d5e.js"></script>

The dependencies you’ve seen before except <a href="https://docs.angularjs.org/api/ng/service/$location" target="_blank">$location</a>. When a form is completed and submitted, I could either give a success message or redirect the user. I decided to redirect them back to the table list once the data was submitted so this is why I needed the <span style="color: #ff0000;">$location</span> service. Next I added my <span style="color: #ff0000;">addTeam()</span> function that we saw before.<script src="https://gist.github.com/Sacamano604/03176e46ae0a3adcc1a1.js"></script>

Within the add team function, I have the <span style="color: #ff0000;">$scope</span> put the data it’s collected from the model into the “<span style="color: #ff0000;">$scope.information</span>” variable. From there I pass it to my php file, and hand off that information. Upon success it takes that information from what it is to JSON, and then the <span style="color: #ff0000;">$location</span> service kicks in and redirects them to the table list. My controller was built.

The last thing I needed to do was to work with the PHP side of things. We had the controller, the route provider and the form to add a team all in place but we needed the bridge between the database and angular. I created another function in our switch. Obviously I gave the case a name of ‘<span style="color: #ff0000;">add</span>’.

<script src="https://gist.github.com/Sacamano604/09a6d2c66af382840d10.js"></script>

To grab the contents from our controller I use the <a href="http://www.php.net/manual/en/wrappers.php.php" target="_blank">php://input</a> stream. This is a read only stream that will allow me to read the data from the requested body...In this case, my form data. After that I push that into the ‘<span style="color: #ff0000;">json_decode</span>’ command to decode it from JSON to an array we can use. I add the following SQL command, to insert the values into the table and match the data with the associated values from our JSON output.

<script src="https://gist.github.com/Sacamano604/6a7cfd191eaf15b078cf.js"></script>

Then after I literally query our database:

<script src="https://gist.github.com/Sacamano604/da66df944aafa97be117.js"></script>

So our whole PHP function looks like this:

<script src="https://gist.github.com/Sacamano604/b59f6962bf9c1413abac.js"></script>

I’m not sure what code will have to be changed and adjusted once the image file is passed through but with the exception of the image field, my form was working nicely.

After the image input works fully, and the details page has all the information we need I will make sure and take the time to clean up the project and comment the code a little better. Next stop, image upload...

<strong>Source Files:</strong> <a href="http://goo.gl/rvObe9" target="_blank">http://goo.gl/rvObe9</a><br />
<strong>Working Project:</strong> <a href="http://bentoussi.com/angularjs/day07/" target="_blank">http://bentoussi.com/angularjs/day07/</a>