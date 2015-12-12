---
layout: post
title: Working with the Blizzard API - The Shallow End
---
Recently I've been itching to work on some more coding side projects. It's been some time since I've made and update to this site, so I thought I'd get both done at the same time.

I've been wanting to work with the <a href="https://dev.battle.net/" target="_blank">Blizzard API</a> for quite some time now, I first came across it a couple of years ago but could never come up with a project to work with it. I figured I should just start small and go from there. With the API you can do all sorts of lookups on character, guilds, progression, etc. Basically if you have a character in World of Warcraft, Diablo, or even a Starcraft account Blizzard keeps that information on hand and makes it available through their API (which is basically the information presented as JSON).

Because I play WoW myself, I chose the <a href="https://dev.battle.net/io-docs" target="_blank">WoW community APIs</a> first. I would do some specific character lookups and out put the data onto a page. There's a massive list that details all of the certain types of methods you can use: achievements, auctions, character profiles, appearance, guilds, mounts, progression, the list goes on.

I chose the smallest method: Character Profile. This gives very basic information on your character (name, level, class, faction, etc). My goal was to have a user lookup a character and display that JSON in a list. If the character doesn't exist then it would display an error.

Here's the Git: <a href="https://github.com/Sacamano604/Blizzard-API-Testing" target="_blank">https://github.com/Sacamano604/Blizzard-API-Testing</a>

Here's the working demo: <a href="http://www.bentoussi.com/blizzardapi/" target="_blank">http://www.bentoussi.com/blizzardapi/</a>

I think I'd like to evolve this project into something bigger. It would be great if I could create some sort of a lookup tool to see if a character that wants to join your guild is suited for the role you need (do they have experience, what's their gear level, etc).

