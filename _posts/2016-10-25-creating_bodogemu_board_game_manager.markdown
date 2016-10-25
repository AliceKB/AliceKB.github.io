---
layout: post
title:  "Creating Bodogemu(board game manager)"
date:   2016-10-25 04:42:20 +0000
---

![](http://imgur.com/FQjFsfx.jpg)

<p>
	 "The app should be a custom app that is created to track something important to you."
 Something important to me? Luckly I had the answer infront of me as I read that sentence.
Board games have always been important to my group of friends, and we would have monthly board game nights. But as our collections of board games grew we started having trouble keeping track of who owned what game. So I instantly knew that this was the perfect job for a CRUD app.</p>

<h2>Planning it all out</h2>
<p>
I started by first listing down the basic things that I wanted the CRUD app to do. I knew it was important for the app to be able to create users and board games. I also needed a user to have a list of the board games they own and to be able to add board games to their list for other users to see. Since multiple people can own the same game, I had to make sure multiple users could add the same game to their list. And I also want a user to be able to see what board games are group up by the companies that own them. So once I had my ideas down, It was time to break into what files I would need to make.
</p>

<h2>Creating the CRUD APP</h2>
<p>
  Going back over my overview, I broke down everything into what I needed to create and do:
</p>	
<ul>
  	  <li>Controllers - Application, User, Boardgame, Company, Type</li>
  	  <li>Models - User, Boardgame, Company, Type</li>
	  <li>Views - Users, Boardgames, Companys, Types, index, layout</li>
	  <li>config.ru, config/enviroment</li>
	  <li>use <code>bundle init</code> to create the gemfile and add gems to it, run bundle install afterwards.</li>
	  <li>Create the Database Folder,models, and assocations, run migrations</li>
</ul>
<p>
Thanks to having a clear list, I was able to break apart the project and slowly build it up. I focused first on building the users model and insuring that I could login and signup. After that it was time to build the Board Game models and so on until I had a version of the Bodogemu app that, while not pretty to look at, worked:
</p>

  ![](http://imgur.com/wQq8xvt.jpg)
  
<h2>Bootstrap</h2>
 <p>
 	While building I focused on making sure that my app was going to above everything else work. But once I knew I had the features that I wanted working, it was time to start focusing on making Bodogemu look better. This in of it self was another challenge for me, considering that I had no idea what I wanted the app to look like in the end or even how to get it there. Thanks to previous lession I knew how to inject css into the pages and how to create a basic layout page using the erb scripting tag and yield. Aside from that I had no idea how to even start. Thankfully after some (a lot) of googling, I started to get used to working with css and the framework Bootstrap. I decided to make Bodogemu in lighter colors to try and get across a playful feeling aswell as keeping the over all appearance nice and simple.</p>
 
  ![](http://i.imgur.com/aOnh3Iw.jpg)

<p>
For now Bodogemu looks great, there are still some more features I want to expand on that I will be working on add. I'm going to get some of my friends to test out Bodogemu and see what else they feel I should add, but for now I am very proud of what I was able to build. So here is a link to the Github repo of <a href="https://github.com/Alicekb/board-game-manager">Bodogemu</a>, feel free to check it out.
</p>
