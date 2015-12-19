---
layout: post
title: AngularJS Services - Part 2
---


I had my first service in place and it was working smoothly. I had to expand on it but I didn’t want to have a lot of factories. The whole point of writing the services was to minimize on code that I was repeating. My plan was to create a few different functions within the team service and call on whichever I would need. I needed to change my current code to facilitate this.

Previously I had a service for the team list and it would perform one function. I changed it so that my service was the ‘<span style="color: #ff0000;">teamService</span>’ and would service all of the functions I would need. Here’s what the new team list service looked like:

<script src="https://gist.github.com/Sacamano604/b1f35828fc02612f1cb8.js"></script>

Great. I had a team service and within it I had a function that would get the teams list. I still needed to add functions for the details, edit, add and delete functions. I worked on this a bit and here’s how it ended up looking:

<script src="https://gist.github.com/Sacamano604/455b69a6278fb741ee46.js"></script>

You can see a lot of similarities from the older code, but it just looks a lot cleaner. I have one service that will take care of all the functions I need performed in relation to the teams.

I still needed one more service. Instead of populating form data in the add and edit controllers I wanted to create ONE service to handle all the form data; collect it, and send it off. For this I would need to send the form data to the service, it would collect it and return it to me.

<script src="https://gist.github.com/Sacamano604/a8c144b05003b6ed996d.js"></script>

The factory is assembling the form data and appending all the fields’ data to the <span style="color: #ff0000;">formData</span> variable. To give you an example of how I used this within the context of a controller, let me show you my edit teams controller since this uses two services.<script src="https://gist.github.com/Sacamano604/bfc85be91512357d7c5b.js"></script>

First I had to edit the controller to use the ‘<span style="color: #ff0000;">teamService</span>’ and ‘<span style="color: #ff0000;">assembleFormDataService</span>’ dependencies. From there I call ‘<span style="color: #ff0000;">teamService.teamsDetails</span>’ and pass it the team’s ID through <span style="color: #ff0000;">$routeParams</span> that we’ve seen before. Then it returns the data back to us so I can pre-fill the form fields when editing a team.

<script src="https://gist.github.com/Sacamano604/548f23d2de6499c7a72b.js"></script>

I needed to send the edited data to the form service so that it could return that to me and I could pass it on to the edit team service. This line is doing that:<script src="https://gist.github.com/Sacamano604/f968db9b56b93b3de01f.js"></script>

You see I call ‘<span style="color: #ff0000;">assembleFormDataService.populateFormData</span>’ and then pass it the data one by one. This service will return the data to me, then I’ll pass it on to the edit team service:

<script src="https://gist.github.com/Sacamano604/47e3166ab818a7d42345.js"></script>

Once successful it will return us to the teams list page. I did not create an if/else statement to handle whether there’s an image already in the database or not. Simply because I’ve limited the add team page to not allow submissions UNLESS there’s an image present. So theoretically any team you edit should always have an image associated with it.

My services are complete and all I need to do is edit some CSS and this will be 100% done.

<strong>Source Files:</strong> <a href="http://goo.gl/NSyDmp" target="_blank">http://goo.gl/NSyDmp</a><br />
<strong>Working Project:</strong> <a href="http://goo.gl/hHLo0B" target="_blank">http://goo.gl/hHLo0B</a>