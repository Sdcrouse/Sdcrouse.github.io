---
layout: post
title:      "MyVerses: A Rails Project of Biblical Proportions"
date:       2020-04-05 02:35:10 -0400
permalink:  myverses_a_rails_project_of_biblical_proportions
---


If you're thinking that's a Bible pun, you're right! For my Rails project, I decided to make an app that lets people create and share their favorite Bible verses. Here's where I got my idea: A few years back, my church had an event where people wrote down a #MyVerse - a Bible verse or passage that they liked and/or identified with - and an explanation of why they chose that verse. They would then put that #MyVerse on one of the walls of the church and/or post it on Facebook for all to see! The issue I had was that it was hard to choose just one Bible verse to be my #MyVerse - there are literally tens of thousands of them! My Rails app solves that issue: instead of requiring users to choose just one #MyVerse, they can write however many MyVerses they want.

Here's how the MyVerses app works. After going to the home page, you can click one of the links on the left to sign up or log in. You can either create an account with the provided form, or you can sign up through Facebook. Once you do, you'll be redirected to your profile, where you can see your account information and the MyVerses that you wrote.

Before I go into creating a MyVerse, I'd better explain my app's model structure. As you might have guessed, I set up the MyVerses app such that a User has many MyVerses, and a MyVerse belongs to a User. However, I realized that a lot of people might choose the same Bible verse as one of their MyVerses - John 3:16, for example. Additionally, there are many versions of the Bible - New International Version, King James Version, ESV, etc. - and not everyone would have the same reasons for choosing that verse as a MyVerse. So, if my app only had a MyVerse and User model, there would wind up being a LOT of similar-looking MyVerses clogging up the database! 

With that in mind, I decided to separate the VerseReference (book, chapter, start of verse, and end of verse) from the MyVerse (version, verse text, and why the User chose that verse as one of their MyVerses). Effectively, the MyVerse model became a join model betweeen Users and VerseReferences. In other words, my models and associations now look like this:

* A User has many MyVerses and many VerseReferences through MyVerses.
* A MyVerse belongs to a User and a VerseReference.
* A VerseReference has many MyVerses and many Users through MyVerses.

> **Side note:** I got experience with Rspec in this project because I decided to write out some tests to make sure that my models and associations were working properly. I also wrote a few tests for some of the views.
> 

Now we can look at creating a new MyVerse. To do this, you can go to the "New MyVerse" page and fill out the form. When you do, you will either be redirected to that new MyVerse's page, or the form will display error messages if you make a mistake.

There are a few things that I should mention about that "New MyVerse" form. Conceptually speaking, it doesn't make any sense (in my mind) to create a VerseReference by itself, and it *really* doesn't make sense to create a MyVerse without a VerseReference, either. Because of this, I have users create a MyVerse and a VerseReference on the same form. So when you create a new MyVerse - or edit an existing one - the app will also either find an existing VerseReference or create a new one, and then associate it with the MyVerse. Also, it is not possible for a user to edit or delete a VerseReference, as that would affect other users' MyVerses. (Note: As a stretch goal, I will have the app auto-delete VerseReferences that have no MyVerses associated with them, in order to keep the database clean.) Finally, I have chosen (for now) to have users manually fill in the data for a VerseReference, instead of choosing from drop-down lists; this will likely change in a later update.

In addition to everything above, you can go to "All MyVerses" to see an index of all of the MyVerses that everyone has created. You can narrow down that list of MyVerses by entering a book of the Bible into the search form at the top; if you enter Genesis, for instance, you will see just the MyVerses whose book is Genesis. Both kinds of lists have links to each MyVerse's page and its user's profile page. 

Each MyVerse's page will display a little bit differently, depending on whether you or someone else wrote it. If you wrote it, you will see buttons that let you edit or delete your MyVerse; these buttons also appear on your profile page. If you are on another user's profile page or on one of their MyVerses' pages, you will not see these buttons. If you're sneaky and try to edit someone else's MyVerse through the URL bar or through the DOM itself, you will likely be redirected with an error message.

You can also go to the "Verse References" page to see all of the VerseReferences that people have created whenever they made a new MyVerse. By clicking on one of them, you can view all of the MyVerses that have that VerseReference. You also have the option of making a new MyVerse with that VerseReference (if you haven't already); if you choose to do this, the VerseReference information will be auto-filled for you on the form.

So, there you have it! That's my Rails project in a nutshell. If I had to give an overall assessment, it was definitely difficult, but I learned a lot. In some ways it was easier than my other projects, and in some ways it was harder; Rails is a HUGE framework, and there's a lot to understand. I think the trickiest parts for me were setting up authentication and authorization (which I can later refactor with gems like Devise and Cancancan), and designing the overall look of the app. Regarding the latter, I had never used Flexbox or Figma before, so this was a new (and helpful) learning experience.

If you want to take a closer look at the MyVerses app, here are some helpful links:

* [MyVerses Github repository](https://github.com/Sdcrouse/my-verses)
* [MyVerses demo video](https://www.loom.com/share/1a1cfaaba80e4f86af2298bc4170c8db)
* [Study group/walkthrough of the MyVerses app](https://www.youtube.com/watch?v=nFCklCUEjuE&feature=youtu.be)
* [My Figma designs of the MyVerses web pages](https://www.figma.com/file/ZVn3NeqHjnaxdM7MqjAjz1/Web-Pages?node-id=0%3A1)

As always, take care, and God Bless!
