---
layout: post
title:      "How I Fixed a Tricky Event Listener Bug in my Project"
date:       2020-07-01 21:44:17 -0400
permalink:  how_i_fixed_a_tricky_event_listener_bug_in_my_project
---


While I was working on my Crazy Coffee Concoctions project (see previous post), I ran into an interesting bug related to event listeners. Here was part of my project plan: When the `index.html` page was initially loaded, it would render a "New Concoction" form by default. When the user submitted the form, it would create a coffee concoction and display it. The user could also click on a "New Concoction" button to generate a new form for creating a concoction. In order for this to work, I attached a listener for the "submit" event onto the "New Concoction" `<form>` element. There was just one problem: The event listener worked on the `<form>` that was rendered by default, but *not* on the `<form>` that was rendered by the "New Concoction" button! In order to solve this bug, I had to learn more about how event listeners work. Later on, I learned that I could make my code even better with event delegation.

## My initial code

Here's a portion of the `index.html` file that was rendered by default:
```
<nav>
	<button>New Concoction</button>
	
	<!-- Other links -->
</nav>
			
<section>			
	<div id="main-container">
		<div>
			<h2>New Concoction</h2>
		</div>

		<form>
			<!-- The rest of the form -->

			<p id="submit-button-container">
				<button type="submit">Create Concoction</button>
			</p>
		</form>
	</div>
</section>
```

Initially, this was the JavaScript that I used to add event listeners to the form:
```
document.addEventListener("DOMContentLoaded", function() {
	 const newConcoctionButton = document.querySelector('nav button');
	 const mainContainer = document.getElementById('main-container');
	 const concoctionForm = mainContainer.querySelector('form');  
	 const newConcoctionHTML = mainContainer.innerHTML;

	 // --------------------------- Additional code ----------------------------------
	 
	 concoctionForm.addEventListener('submit', createConcoction);
	 newConcoctionButton.addEventListener('click', () => mainContainer.innerHTML = newConcoctionHTML);
});
```

Here's how I thought this would work: I would get the `newConcoctionButton`, the `mainContainer`, and the `concoctionForm`. Then, I would call my `createConcoction` function as soon as the "submit" event fired on the `concoctionForm`. I would then replace the `mainContainer`'s inner HTML - which consisted of the `concoctionForm` and its heading - with information about the new concoction. In order to preserve the HTML for that form and heading, I made a copy of it. Then, when a user clicked on the `newConcoctionButton`, all I had to do was replace the `mainContainer`'s inner HTML with that copy of the original HTML.

This idea worked...partially. When I loaded the page, filled out the "New Concoction" form, and submitted it, everything worked just fine. But when I clicked on the "New Concoction" button, filled out the form, and submitted it...nothing happened! Why was that? What was going on here?

## Solving the bug

After I did a little research into event listeners, the truth finally hit me! Take a look again at these lines of code:
```
const concoctionForm = mainContainer.querySelector('form');  
const newConcoctionHTML = mainContainer.innerHTML;

concoctionForm.addEventListener('submit', createConcoction);
newConcoctionButton.addEventListener('click', () => mainContainer.innerHTML = newConcoctionHTML);
```

It turned out that even though the `mainContainer` had the exact same inner HTML when the page was first loaded, and after the user clicked on the `newConcoctionButton`, *there were two separate forms being generated!* The listener for the "submit" event had been attached to the `concoctionForm` when the page was first loaded, but it was *not* attached to the form that got rendered when the user clicked on the `newConcoctionButton`.

To fix this bug, I attached a separate event listener to the form that got rendered by the `newConcoctionButton`:
```
// Same code as before:
document.addEventListener("DOMContentLoaded", function() {
	 const newConcoctionButton = document.querySelector('nav button');
	 const mainContainer = document.getElementById('main-container');
	 const concoctionForm = mainContainer.querySelector('form');  
	 const newConcoctionHTML = mainContainer.innerHTML;
	 
	 // --------------------------- Additional code (as before) ----------------------------------

	 concoctionForm.addEventListener('submit', createConcoction);

	 // Modified code:	 
	 newConcoctionButton.addEventListener('click', function() {
		 mainContainer.innerHTML = newConcoctionHTML;

		 mainContainer.querySelector('form').addEventListener('submit', createConcoction);
		 // This fixes a tricky bug: In this case, mainContainer.querySelector('form') !== concoctionForm!
	 });
});
```

This works, but it's kind of annoying having to add the same event listener to multiple forms with the same HTML. Is there a cleaner way to do this? As it turns out, there is! I can refactor my code with event delegation.

## Refactoring with event delegation

I won't go into too much detail here about event delegation, but the idea is that instead of adding event listeners to individual elements, you can add *one* event listener to a *parent* element. Then, when a child element is clicked, the event bubbles up to the parent element that has the event listener. This technique is often used on lists: Instead of adding/deleting event listeners on individual `<li>` items that get created and/or deleted, you can simply add a single event listener to the parent `<ul>` or `<ol>` element. That makes your code cleaner and much more flexible! More information about event delegation is available in the Resources.

Here's how I refactored my code with event delegation:
```
document.addEventListener("DOMContentLoaded", function() {
  const newConcoctionButton = document.querySelector('nav button');
  const mainContainer = document.getElementById('main-container');
  const newConcoctionHTML = mainContainer.innerHTML;
	
	// --------------------------- Additional code ----------------------------------

  mainContainer.addEventListener('submit', createConcoction);
  
  newConcoctionButton.addEventListener('click', () => mainContainer.innerHTML = newConcoctionHTML);
});
```

Instead of attaching the "submit" event listener to individual forms, I simply attached it to their parent element, the `mainContainer`. This gave my code the following benefits:
1. It made my code a little more DRY
2. It made my code more flexible
3. It prevented me from having to use up extra memory to store the "New Concoction" form

> **Side Note:** This works for right now because only ONE child element (the "New Concoction" form) triggers the "submit" event. If multiple child elements were able to trigger the "submit" event, I would need to identify which one triggered it.

So, there you have it! That's how I solved an event listener bug in my project and refactored my code with event delegation. I hope this helps you as much as it helped me. Take care, and happy coding!

## Resources

* [How JavaScript Event Delegation Works](https://davidwalsh.name/event-delegate)
* [Understanding Event Delegation](https://learn.jquery.com/events/event-delegation/)
