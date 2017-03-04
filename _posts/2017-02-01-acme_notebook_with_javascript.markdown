---
layout: post
title:  "Acme Notebook with Javascript!"
date:   2017-01-31 22:32:35 -0500
---

After I build my Acme Notebook project, I started on the javascript portion of my lessions and was then tasked with adding Javascript to my rails project. Part of the assignment was to make sure that I had an index page and a show page rendering through javascript after calling the database. This blog post is going to be about how I changed my main page to use Javascript to update the page.

Here is a quick recap of what features the Acme Notebook has:
* The Acme Notebook has Vistors, Users, and Admins.
* Vistors can only see the homepage, log-in page, and Sign-up page.
* Users can see and edit their homepage, their own notes, see shared notes, and any comments in those notes.
* Admins can see everything and edit everything as well as delete users.

So the first thing I needed to do was get the User show page ready. Which I did by removing the erb that went through the page adding the notes, instead I replaced the code with a simple div with an id. This div was now going to be where I was going to add all the html for my notes. Now in order to actually create and render each Note I wrote an ajax call to the /notes route:

app/asses/javascript/notes.js

```
let getNotes = function() {
  $.ajax({
    url: "/notes",
    method: "GET",
    dataType: "json"
  })
  .success(function(json){
    renderNotes(json.notes);
    noteListener();
  });
};
```

app/controllers/notes_controller.rb

```
def index
  @notes = Note.all_by_user(current_user.id)
  render json: @notes
end
```

The /notes route when called finds all the notes by the current user. It does this by calling the all_by_user method in the Note class that find all the notes that match the current user. After it does this it then returns these notes in a nice JSON format. The serializing of the actual Note models is all handled by the Active Model Serializers gem. With the Json response send back the the ajax call, the next step was to actually render the Notes and add them to the User show page. Since the JSON response was a collection of all the notes that a User had, I needed to cycle through the collection and create a new Note object. Each Note finally had to be passed into handlebars compile inorder to get back the html for each Note that would be stored in an array called Notes. Finally once the loop had finished going through the collection, the new array filled with the notes html is added to the main User show page div.

app/asses/javascript/notes.js
```
function Note(attributes){
  this.id = attributes.id;
  this.title = attributes.title;
  this.content = attributes.content;
  this.viewers = attributes.viewables;
  this.comments = attributes.comments;
}

let renderNotes = function(array) {
  let notes = [];
  for(i = 0; i < array.length; i++) {
    let note = new Note(array[i]);
    let noteHtml = note.renderNotesHtml();

    notes.push(noteHtml);
  }
  $(".notes").html(notes);
};
```

With the User show page now retriving all the User's current notes it was easy to update the rest of the app's features to render to the same page. The new Note modal button on the page went from reloading the page to instead just appending the new note to the main page. Clicking on a note updated the main page to display the note along with its comments and its list of shared with. Added a new comment also just added it to the current note with out reloading the page. Now that my main page was updated to use Javascript, I had the foundation in place to update the rest of my app. 
