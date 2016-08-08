---
layout: post
title:  "CLI Gem Project"
date:   2016-08-08 03:09:49 +0000
---

  This week my assignment for the Flatiron School is to create a CLI Gem. It has to be able to be packaged as gem, provide a gem installation and provide data from an external source. Also It needs to be able to drill into a specific item if the user wants more information. So after some thinking, I decided on building a CLI about video game releases dates. I want to be able to get video game releases from the CLI and then be able to find more information about a specific game.

  The first thing I had to figure out was just how to build a gem from scratch. Lucky for me in the CLI lesson plan there was as link to a video walk-through of building a CLI Gem called Daily Deal. Using that as a starter base I build up my app first with what I wanted to it show without worrying about actually coding it first. This meant that I had to think about my end result and build a concept of what I wanted the CLI to display. Doing it this way really helped to break down the steps and kept me from trying to do everything right from the beginning.

  So for my CLI gem I wanted the User to first be asked what kind of system they would like to search for, this would present them with options to chose from. Then based on that choice they could select the month they want to see the results for. The last thing they should be able to do was select the game they would like to learn more about. Like this:
> ** What system would you like to look for? **
> PC  || Xbox One || PS4 || Exit
> 
> **What month would you like to see?**
> January        May          September
> February       June         October
> March          July         November
> April          August       December
> 
> **MAY - PC**
> 
> BATTLEBORN – MAY 3
> FINAL FANTASY 10/10-2 HD REMASTER  – MAY 12
> DOOM  – MAY 13
> HOMEFRONT: THE REVOLUTION – MAY 17
> SHADWEN – MAY 17
> FALLOUT 4: FAR HARBOR DLC – MAY 19
> 
> **BATTLEBORN  - PC**
> Set in a distant future, the only hope for the last star in a dying universe is a new breed of warriors who must put aside their differences to drive back an unstoppable menace. Players choose from a myriad of powerful heroes and fight together alongside their friends in a narrative-driven co-operative campaign, or battle against them in fast-paced competitive multiplayer matches.
Now that I had the concept down, It was time to start building the Gem. I found that having something to use as a reference was really helpful here since I could break down each section and just build one part at a time. For the systems and months this involved creating the output strings and asking the User for input then I had to make sure to write checks that would would keep the User from entering something invalid. For the checks I decided to create arrays that would hold all the valid options and then check if the input was included in the corresponding array. To make it easier to check I made sure to ensure that the input was turned into uppercase so that it was easier to match.

  With that out of the way it was time to build the actual scraper that was going to give me back the resulting list. After some searching I found a page that not only listed the releases but looked like it was being updated in a consistent matter. Using Nokogiri, openHTML, my browser’s inspector tool, and a lot of trial and error I narrowed down the selectors for each line of videogames with their systems and release dates. I had the scraper return an array so that it would be easier to search through.

  Thanks to the scraper I now had a list that would show strings with the videogame, its system and the release date. But it was showing every videogame in the array and I needed to narrow it down to just the month that the user was asking for. So using the #each method and #include? Method I was able to cycle through each of the items in the original array and then check if the User’s month and system inputs were included in the string. If there was a match then that string would then pushed into a new array that would be returned at the end.

  The next part I had to build was a way to have the User pick a game to learn more information about. Thanks to already having an array with a month’s videogame releases all I needed to do was create the output asking for the user’s input and the actual serach function. The search function just had to taken in the user’s input and match it to the corresponding index and then input that name to find the correct summary for the game. Luckly while searching for the release games website before I found an API that would return information about a videogame in an XML format. Since I already had a scraper I decided to just upgrade it to take in an input and serach the API and find the summary of a given game. Which didn’t work at first because I forgot the string was including not just the name of the game but its system and release date. So using gsub, I selected out the system and release dates in the string and then was able to just use the name of the game.

  Lastly, while my gem was working out pretty great it was still only able to select one game once with the User having to start it all over if they wanted to select a different one. So inorder to make it easier on the User, I went back through my code and added options for the User to be able to select multiple games and then an option to ask if they would like to select a different month. With this my gem had all the functions that I had set out to create. Everything was displaying exactly like my concept at the beginning. Now I am still making improvements on the gem and fixing any errors that I find but I am really happy with how it all came together. There were some frustrating moments but I ended up learning a lot and reinforced the knowledge that I had been building over the past lessons.**
