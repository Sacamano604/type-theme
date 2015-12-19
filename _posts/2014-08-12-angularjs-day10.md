---
layout: post
title: Learning AngularJS - Day 10
---

Adding the functionality to delete teams was the last task at hand. In my <span style="color: #ff0000;">teamTemplate.html</span> file I went ahead and put some code behind the delete button itself. From previous posts, I created everything needed for the edit button but this time I’ll be returning to the second button on the page. So just like the edit button, I had the delete one point to it’s own view and pass the team id on to it.

<script src="https://gist.github.com/Sacamano604/d7500ed8894252d30892.js"></script>

In my <span style="color: #ff0000;">footballApp.js</span> file I went ahead and added the route to the delete page.

<script src="https://gist.github.com/Sacamano604/f6b2a7e1bfdfb5edc2fa.js"></script>

The reason why I’m creating a whole page to delete a team is to give the user a confirmation, or a second chance to ‘opt out’ if you will. This way users won’t click on delete by accident and have the team disappear on them immediately.

From here I added the <span style="color: #ff0000;">deleteTeamController</span> to my <span style="color: #ff0000;">footballControllers.js</span> file.

<script src="https://gist.github.com/Sacamano604/d3410963fde828904fbb.js"></script>

As before I’m using <span style="color: #ff0000;">routeParams</span> to pass the team ID through so that on the delete page I can confirm to the user the team they’re deleting (which is why you see me calling from the detail case on the php switch). From there when they click on the ‘<span style="color: #ff0000;">deleteTeam()</span>’ function, we’ll pass the team ID through to the teams.php file. Lastly we’re then redirecting the user back to the teams list, almost working as a confirmation that the action’s been completed. For the <span style="color: #ff0000;">deleteTeam()</span> function I needed to create a confirmation page, which would obviously correspond with my views. Here’s what <span style="color: #ff0000;">deleteTeam.html</span> looked like:

<script src="https://gist.github.com/Sacamano604/e69da61de277d1c2857f.js"></script>

Once the confirmation “Yes, Delete” is pressed it’s going ahead and passing the team ID that needs to be deleted to the PHP file. If no is pressed, it simply takes the user back one page (just like the back button in their browser).

Next I added a case to my php switch, which was probably the easiest part of the whole project.

<script src="https://gist.github.com/Sacamano604/442c4ed57efcf431966e.js"></script>

Get the ID that’s passed, and delete it from the teamlist where the ID is the ID that’s passed.

This project is very close to being finished and is actually something I’ll wrap up today. It just needs some tidying up, and I need to populate the rest of the team information.

<strong>Source Files:</strong> <a href="http://goo.gl/CcjLmP" target="_blank">http://goo.gl/CcjLmP</a><br />
<strong>Working Project:</strong> <a href="http://goo.gl/8bLMuf" target="_blank">http://goo.gl/8bLMuf</a>