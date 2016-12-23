---
layout: post
title:  "Acme Notebook Project"
date:   2016-12-23 15:13:54 -0500
---


<p>For my assessment I was tasked with building an application that manages related data. After some thinking I decided that I wanted to build a notebook application. The idea came to me while listening to a podcast where the panelist dicussed the importance of teams keeping up to date with each other's notes for a project. So I knew I wanted to build an app that would allow a user to create a note that can be shared and commented on my multiple team members.</p>

  <p>
    Now usually I just write out a blog post going over the main concepts and thoughts as I was building my project, but this time I decided I wanted to split this blog post into three post. I wanted each blog post to focuse on a different part of my process building the app. This being the first post in the series, it will focuse on the process of planning out, as I later named it, the Acme Notebook. The second post will focus on the actual coding of the project, while the last post will be on the styling. So lets begin with the first step:  </p>

<p>First you needed to decide what the goals of your project are, this will help inform the rest of your decisions. </p>
    <ul>
      <li>The goal for the Acme Notebook Project was to create a place where teams can go to share notes among themselves. </li>
    </ul>
		
 <p>After you have your goals, the next important thing to do is decide on the roles. Who is going to use you project and are they going to see different things?</p>
  <ul>
    <li>The Acme Notebook is going to have Vistors, Users, and Admins.</li>
    <li>Vistors should only be able to see the homepage, log-in page, and Sign-up page.</li>
    <li>Users should be able to see and edit their homepage, their own notes, and only see shared notes, and any comments in those notes.</li>
    <li>Admins should be able to see everything and edit everything as well as delete users.</li>
   </ul>
<p>Finally you need to list out the features of your project. What are the basic interactions?</p>
    <ul>
      <li>Users: Registration, creating/editing notes, sharing notes, creating/editing comments.</li>
      <li>Admin: Moderating any user content</li>
    </ul>
		
<p>The next step in my planning phrase was to write a list of user stories. A story represents an interaction from a single user's perspective. While writing these stories you need to answer the questions of Who is this for? What do they want to do? Why do they want to do it? These three questions are important to answer.</p>
    <ul>
      <li>As a User, I want to be able to create a note so that I can view it later.</li>
      <li>As a User, I want to be able to share a note so that another user can see it.</li>
      <li>As a User, I want to be able to visit a shared note so that I can leave a comment for the note owner.</li>
      <li>As an Admin, I want to see a list of Users so that I can delete a User, their notes, and their comments.</li>
      <li>As an Admin, I want to be able to edit or delete another User's note/comment so that I insure it meets a standard.</li>
    </ul>

<p>After the goals, roles, features, and user stories, I found that it helps me in getting started if I have solid understanding of the tables and associations before I begin coding.</p>
<img src="http://i.imgur.com/LwCcejB.png" title="source: imgur.com" height="400" width="500"/>
	
  <p>So that in a nutshell was how I want about planning out the Acme Notebook Project for my rails assessment. Having a clear plan set in place before starting any coding really helped me approach the project with more confidence. Of course there were a couple of things that came to me as I was working on the project that caused me to make changes to my inital plan, but that is something I will talk about in the next part of this blog post series.</p>
  
  <p> As to why I named it Acme Notebook:</p>
>     Whenever we played a game where we had a grocery store or something we called it the ACME corporation. Why? Because in the yellow pages if you looked, say, under drugstores, you'd find the first one would be Acme Drugs. Why? Because "AC" was about as high as you could go; it means the best; the superlative.
  - Chuck Jones in a 2009 documentary
