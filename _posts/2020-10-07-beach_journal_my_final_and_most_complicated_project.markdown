---
layout: post
title:      "Beach Journal: My Final (and Most Complicated) Project"
date:       2020-10-07 03:43:54 -0400
permalink:  beach_journal_my_final_and_most_complicated_project
---


**Overview:** I love going to the beach! There's so much to see and do, from the beach itself to restaurants, lighthouses, shops, and a whole host of other stuff. One of my favorite activities is to keep a journal of my beach trips; that's always fun to read later, and it gives me a good idea of what to do and where to go the next time I visit. For my React/Redux project, I decided to make an online version of a beach journal, so I can use it wherever and whenever I want. It also makes it a lot easier to put all of the information about different beaches in one place.

## The Original Idea

Originally, I had wanted to make an app called a Beach Blog, where users could write posts about their favorite beaches and compare notes with each other. However, by necessity this would have required user signup, login, authorization, authentication, etc. I would have also needed to figure out how to set up the beaches: Do I have a default list of beaches with a name, location, and description? Do I allow certain users to CRUD beaches, while others can only add a blog post about that beach? Ultimately, I realized that this would have made my app far more complex and difficult than it needed to be. I decided to scale it back a little and make a Beach Journal instead, and to not include user signup/login functionality. However, I still like the idea of a Beach Blog, so that will likely be a later version of this app; it could even be a separate app altogether, but it would be connected to the Beach Journal.

## Beach Journal App Features
The way that I set up this app, users will first have to create a beach if this is their first time using it; it didn't make sense in my mind for a user to write a journal entry for a nonexistent beach. To create a beach, users go to the "New Beach" page. On the form, they can fill out a beach's name, location, and other information such as items to bring to a beach and popular activities. They can also add attractions, which are then sorted by category when they view a beach. For instance, users could write names and descriptions for different restaurants, all under the same "Restaurant" category. Or they could make a Wildlife category and list all of the different seabirds that they've seen at a beach.

Once users submit the "New Beach" form, they will be redirected to a list of their saved beaches. To view the beach that they've created, they can click on the corresponding "View Beach" button. The information about that beach (basic info, attractions, journal entries, etc.) is then displayed on that page. From there, users can create a new journal entry by clicking on the "New Journal Entry" button, which renders a form. The "New Journal Entry" form requires users to enter a date and text for a journal entry, but they can also add a title and list of topics if they want to make the journal entry more like a blog post.

At this time, users can also delete any of their journal entries, but they cannot delete beaches or edit their beaches and journal entries. I will enable this in a future version of the Beach Journal app.

## The Process
### Models, Serialization, and Normalization

The model structure that I came up with looks like this:
* A Beach belongs to a Location and has many Attractions and Journal Entries
* A Location has many Beaches
* An Attraction and a Journal Entry belong to a Beach

To limit the number of fetch requests to the server, I decided to have the app, when it first loads, fetch all of the beaches and their associated locations, attractions, and journal entries from the server. I learned the hard way that while it's easy to make a has_many/belongs_to relationship on the backend, it's incredibly difficult to structure and serialize the data in such a way that it's easy to store and use on the frontend. From the [documentation I found](https://redux.js.org/recipes/structuring-reducers/normalizing-state-shape), it is also recommended that you normalize JSON data on the frontend in order to (at least in theory) make it easier to store and use with Redux. I say "in theory" because I had a lot of trouble trying to find a normalization Node.js package that worked well with a Ruby serialization gem.

Initially, I used the [Fast JSON API gem](https://github.com/Netflix/fast_jsonapi) to serialize my data, and I tried out the [Normalizr Node package](https://github.com/paularmstrong/normalizr) to normalize that data on the frontend. However, I had a lot of trouble getting those two libraries to mesh well. I ultimately decided to keep using the serialization gem, but to write my own normalization function; by then, I knew full well how I wanted to structure my data, so it wasn't difficult to write. I will likely write another blog post that goes more in depth on how I serialized and normalized my data; for the sake of brevity, I won't include that information here. One thing I will say, though: The [JSON Viewer Chrome extension](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US) (combined with the `rails s` command) and `console.log()` helped a lot with fine-tuning my data structures.

### A lesson learned is soon returned; a lesson lived is wisdom giv'd.

There is a lot to learn when it comes to React and Redux, so it's easy to forget something here and there. But one thing I would recommend *not* forgetting is how to properly update state in a Redux reducer. That would have saved me a lot of headache with a problem that had me stumped for a while. It happened while I was trying to delete a journal entry from state after deleting it from the backend.

Here's an example of how I structured my state for journal entries:
```
Beach entries:

{
  1: {
	       id: 1,
	       beach_id: 2,
				 date: "September 25th, 2020", 
				 entry_text: "Lorem ipsum dolor sit amet.",
				 title: null,
				 topics: null
	},
  2: {
	       id: 2,
				 beach_id: 3,
				 date: "October 6, 2020",
				 entry_text: "I visited this beach once, with the Beach Boys. Off the Florida Keys, there's a place called Kokomo. That's where we wanna go to get away from it all.",
				 title: "How to Quickly Get a Song Stuck in Your Head",
				 topics: "Songs, beaches, Beach Boys"
	}
}
```

Let's say we wanted to delete the first journal entry. We would send the corresponding reducer an action like this: `dispatch( { type: 'DELETE_ENTRY', 1 } )`.

Initially, the corresponding reducer action looked like this:
```
const journalEntriesReducer = (state = {}, action) => {
  switch(action.type) {

	  case('DELETE_ENTRY'):
		  delete state[action.id];
			return state;
					
  }
}
```

The problem was that even though I was successfully removing a journal entry from state, the page with the journal entries wouldn't re-render to reflect the changes. I had to refresh the page - or navigate to another page and then back to it - to see the changes.

I had forgotten that when the state is a mutable object like an array or hash,  re-rendering only happens if the reducer returns a new state, instead of the original (albeit now mutated) state. What I needed to do instead was make a copy of the state and mutate *that*. Here is the updated code that works correctly:
```
const journalEntriesReducer = (state = {}, action) => {
  switch(action.type) {

    case('DELETE_ENTRY'):
		  let updatedState = {...state};
			
			delete updatedState[action.id];
			
			return updatedState;
			
  }
}
```

This was a tricky bug, but solving it reinforced a lot of what I learned about Redux state and reducers.

I solved quite a few other problems while making this app as well, but I would need to write a lot of blog posts to cover them all! The examples that I showed above were definitely some of my biggest challenges, though.

## Reflection

In retrospect, I made this app more complicated than it needed to be. I intend to update it for simplicity and to make it a little more user-intuitive. However, this process taught me a lot about the pros and cons of Rails, React, and Redux, especially with regards to how to properly structure my data on the frontend and backend. I don't regret the learning experience one bit.

Also, I had some fun with the overall visual design of the app. By using a combination of CSS and the React-Bootstrap Node package, I was able to structure the app so that it looked visually appealing (centered content, separating related content into their own rows and columns, etc). I also gave it plenty of "beach colors", so to speak. It got tricky since I had never used React-Bootstrap before, but I'd say it was worth the effort.

I'm glad I was able to make a Beach Journal for my final project at Flatiron. The process wasn't easy, but I like the result a lot! This is definitely an app that I will use in the future. To all who are reading this: I hope you are able to enjoy the app as much as I have.

Take care, and God Bless!

## Resources
1. Beach Journal frontend: [https://github.com/Sdcrouse/beach-journal-client](https://github.com/Sdcrouse/beach-journal-client)
2. Beach Journal backend: [https://github.com/Sdcrouse/beach-journal-backend](https://github.com/Sdcrouse/beach-journal-backend)
3. Beach Journal Demo video: [https://www.loom.com/share/dfdc7f0bdced4f13bc0c6f935c38e892](https://www.loom.com/share/dfdc7f0bdced4f13bc0c6f935c38e892)
4. Normalizing state in Redux: [https://redux.js.org/recipes/structuring-reducers/normalizing-state-shape](https://redux.js.org/recipes/structuring-reducers/normalizing-state-shape)
5. Normalizr Node package: [https://github.com/paularmstrong/normalizr](https://github.com/paularmstrong/normalizr)
6. Fast JSON API gem: [https://github.com/Netflix/fast_jsonapi](https://github.com/Netflix/fast_jsonapi)
7. JSON Viewer Chrome extension: [https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh?hl=en-US)