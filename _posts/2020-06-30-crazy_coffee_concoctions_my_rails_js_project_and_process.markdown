---
layout: post
title:      "Crazy Coffee Concoctions: My Rails/JS Project and Process"
date:       2020-07-01 02:32:41 +0000
permalink:  crazy_coffee_concoctions_my_rails_js_project_and_process
---


For my Rails with JavaScript project, I decided to make a more specialized version of my Sinatra project. For my Sinatra project, I had built an app called Recipe Rolodex, which allowed users to create, read, update, and delete their own recipes, and view the recipes that other users had created. My Rails with JavaScript project focuses specifically on coffee, so I am calling it Crazy Coffee Concoctions. Making this app has been quite the process!

## Crazy Coffee Concoctions in a nutshell

Crazy Coffee Concoctions is a single-page application (SPA) that uses HTML, CSS, and JavaScript for its frontend, and a Rails API for its backend. It allows users to write and save whatever crazy coffee ideas that they can think of. They can give their concoctions names, coffees, a whole bunch of ingredients sorted by category (liquids, sweeteners, creamers, etc), instructions, and notes. They can also view a list of their saved concoctions. Since this is an SPA, all of this happens on one page, so no need to wait for the page to reload between saving and viewing a coffee concoction!

The one exception to this is the HTTP error status pages that I added: 404 Not Found, and 418 I'm a Teapot. The latter HTTP status is a fun little April Fool's Day easter egg that I discovered. It says that the server is, permanently, a teapot, and you can't brew coffee with a teapot. To get that error status, just write "Brew coffee with a teapot" and/or "Change server into a teapot" in the instructions. To get back to the app, click on the "Refresh" button in your browser.

## The coding process

When I first started this project, I wasn't sure at all where to begin! Do I make the Rails backend first, with all of its migrations, models, controllers, etc? Do I start with designing the HTML/CSS? What's the right way to go about this? The best solution for me, as it turned out, was to go at it from a different angle altogether. It was all thanks to a set of Rails/JavaScript project build videos.

The videos followed this structure for building out a project:

### Planning

1. Look over the project requirements (that's a given)
2. Figure out what sort of project you want to build - what's your project domain, and what do you want it to do?
3. Write out your user stories for the project
4. Based on those user stories, wireframe your project (models and associations - Draw.io is a good program for doing this)
5. Determine what your MVP (Minimum Viable Product) should be; your other project ideas/features should then be stretch goals
6. Figure out what you want the user interface to look like - Figma is a good tool for this

### Setup

This is the part that helped me the most with structuring my project. In summary:

1. Create two Github repositories: one for your frontend, and one for your backend. This is good practice, because if you choose to deploy your project, you may wish to use your frontend with Heroku's server, or your backend with a Netlify frontend. This is much easier to do if your frontend and backend are in separate repositories.
2. Instead of building *horizontally* (all your models, all your controllers, all your HTML/CSS), build *vertically* (one feature at a time - one model, one controller, one view). This ensures that you don't write more code than you need, and it's much easier to keep track of everything.
3. Use a separate Github branch for each part of a feature: "model-1", "controller-1", "view-1", "refactoring", etc.

*Side note*: They recommend initializing the backend repo, coding a feature for it, then initializing the frontend repo and coding the corresponding feature. I personally think it's OK to make both repositories - one after the other - each with a basic skeleton/structure, just to have everything on hand. Either way is fine, as far as I can tell.

### Coding the Backend

This is a recommended order of operations, but you can modify it as you see fit (such as building two models and associating them with each other):

1. Build out *one* migration, model, and related associations, and test them out in the console
2. Build out *one* route, controller, and controller action
3. Serialize your returned JSON data (you can build your own serializer or use something like the `fast_jsonapi` gem). Make sure that when you navigate to a route, the JSON is structured the way that you want it to be.
4. Merge your feature branch with `master` and move onto the frontend.

### Coding the Frontend

Again, this is a recommended order of operations; your mileage may vary:

1. Set up the frontend with a simple `index.html` file, `style.css` file, and `index.js` file. Make sure that they work as expected.
2. Add a `DOMContentLoaded` event listener with a simple `console.log` statement in your `index.js` file.
3. Set up CORS (Cross-Origin Resource Sharing) on the backend (see Resource 1 for more information).
4. Use a simple fetch request (`GET` is the recommended HTTP verb for the first fetch) to connect your frontend with your backend.
5. Manipulate the DOM with the returned JSON data.
6. Refactor your code wherever it's needed.

Repeat this process for the rest of your MVP features (except for the initialization/setup steps).

They recommend building out all of your features with JavaScript functions, and then refactoring with Object-Oriented JavaScript. This may or may not work for you. For me, it was tricky to figure out which functions should be methods of a JavaScript class. In retrospect, it may have been better for me to program with OOJS from the get-go, since the project required it. Word of advice: if you go from functional to object-oriented JavaScript, save the DRY refactoring for the OOJS; otherwise, you may find that some of your refactoring works for functions, but *not* for object orientation.

The last step is to code any stretch goals you have time for. You could even try using a CSS framework such as Bootstrap.

Again, this is only a summary; more details can be found in the Resources.

## Reflection
Crazy Coffee Concoctions was a pretty fun project to make; I'll definitely be using it in the near future to store my coffee ideas. Planning it was the key. The user stories and wireframing helped a lot because they gave me a good structure for my project. I was able to split it up into different steps, and I had some visuals to reference as I build out the HTML, CSS, and JavaScript. And again, the project videos were *super helpful* because they showed me a good way to design my project without getting lost in the details.

It was definitely interesting to use multiple languages in one project, especially when it comes to something like Array manipulation; some Array methods are easier with Ruby, while others are easier with JavaScript. As for object orientation, I can't say whether one language is better than the other; Ruby and JavaScript have their own strengths and weaknesses.

If I had to do this project again, I would probably (as I mentioned earlier) start with OOJS instead of functional JavaScript. It was tricky to transition from one format to the other, although it gave me a good appreciation of how JavaScript works. Additionally, I would use a CSS framework like Bootstrap to make things simpler; the CSS styles that I needed were tricky to code.

Thank you for reading over my project blog post! I hope you find it helpful whenever you make a Rails/JavaScript project. Stay safe, and happy coding!

## Resources
1. [JavaScript Project Setup](https://github.com/AyanaZaire/seeda_syllabus_frontend/blob/master/js-project-ooo-frontend.md)
2. [Rails/JS Project Build, Part 1](https://www.youtube.com/watch?v=Q5R7HSqdGFk&feature=youtu.be)
3. [Rails/JS Project Build, Part 2](https://www.youtube.com/watch?v=sLrFiwhMPZU&feature=youtu.be)
4. [Rails/JS Project Build, Part 3](https://www.youtube.com/watch?v=2xvuGWI3H58&feature=youtu.be)
5. [Rails/JS Project Build, Part 4](https://www.youtube.com/watch?v=oUiLxmgOvJ8&feature=youtu.be)
6. [Project Setup Example](https://github.com/learn-co-curriculum/mod3-project-week-setup-example)
7. [Project Planning Tips](https://github.com/learn-co-students/js-spa-project-instructions-online-web-sp-000/blob/master/project-planning-tips.md)
8. [Crazy Coffee Concoctions Backend](https://github.com/Sdcrouse/crazy-coffee-concoctions-backend)
9. [Crazy Coffee Concoctions Frontend](https://github.com/Sdcrouse/crazy-coffee-concoctions-frontend)
10. [Crazy Coffee Concoctions Demo Video](https://www.loom.com/share/0c1ec46b01a0444384c4e96cfb44f963)


