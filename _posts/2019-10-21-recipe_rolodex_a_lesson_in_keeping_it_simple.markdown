---
layout: post
title:      "Recipe Rolodex: A Lesson in Keeping it Simple"
date:       2019-10-21 04:30:03 -0400
permalink:  recipe_rolodex_a_lesson_in_keeping_it_simple
---


**Introduction:** For my Sinatra project, I created a Recipe Rolodex app. Rolodexes were often used to organize business contacts, but I figured that the same could be done for recipes; thus, the name of the app. Oftentimes, people write or print off recipes and store them somewhere, but they can get easily lost and disorganized. The Recipe Rolodex lets you store and organize your recipes all in one place for easy access at any time! In this post, I will further explain how my app works, some of the problems I had to solve, how I learned the importance of keeping my projects simple, and my future plans for the Recipe Rolodex.

## An overview of the Recipe Rolodex

As an example of what the Recipe Rolodex looks like, here is a screenshot of the login page:

<img src="https://doc-04-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/2n1ldos6pq055ek6jlh3kntfirp6n3l0/1580083200000/18375684649449857957/18375684649449857957/1hnYr5LjZf-kbUBqGiVqLcKkwXxPoZT8l?e=view&authuser=0&nonce=0e6fk5pfbr5uk&user=18375684649449857957&hash=45qpst1fh07jk134g6lk31co70jsua52" alt="Recipe Rolodex Login Page" width="800" height="400" />

The Recipe Rolodex is a CMS (Content Management System) built with Sinatra. Users are able to create an account, log in and out, and CRUD (Create, Read, Update, and Delete) their own recipes. There are quite a few validations in place as well. For instance, users cannot log in without a username and password, and while they can view other users' recipes, they can only create, edit, and delete their own. If they try to log in with invalid credentials and/or change someone else's recipe, they will be redirected to another page with an error message. There are also validations on the User and Recipe forms (required fields, the format of a username, etc).

I had fleshed out a lot of ideas for the Recipe Rolodex app on paper ages ago, but they turned out to be harder to code than I had expected. This is where the KISS principle (Keep It Simple, Stupid) came in...or should have. My app got increasingly complicated when I changed my model structure, although I had a good reason for doing so.

## The model structure

The Recipe Rolodex originally had two models: User and Recipe. Users had many recipes, and a recipe belonged to a user. However, recipes usually have multiple ingredients, each ingredient having a name, amount, brand, etc. Because of this, it became clear before I even started the project that I needed an Ingredient model. A recipe had many ingredients, and an ingredient belonged to a recipe. But this introduced *another* problem: it was now possible for users to create ingredients with the same name over and over again. So, I added a RecipeIngredient JOIN model. My final model structure looks like this:

* A recipe has many ingredients through recipe_ingredients.
* An ingredient has many recipes through recipe_ingredients.
* A recipe_ingredient belongs to a recipe and an ingredient.

Ingredients now only have names and ids, while recipe_ingredients have amounts, brand names,  ids, recipe_ids and ingredient_ids.

## The recipe and ingredient validations

Here is how I set up the ingredients in my recipe forms: The user can create up to five ingredients and add any additional ingredients to the "Additional Ingredient" field. Bearing that in mind, this is where my validations got "interesting". I wanted to ensure that a recipe had at least one ingredient, and that users would not be able to create ingredients without names; if they added amounts and brands, but no names, then they would be redirected back to the "new recipe" or "edit recipe" forms with an error message.

This is when I researched ActiveRecord validations, even though I hadn't gotten to that point in Flatiron's Fullstack Web Development curriculum yet. Validations simplify a lot of things. For example, instead of writing conditional statements and error messages, I can simply add a macro such as this to one of my models: 
```
validates :name, presence: true
```
This prevents an object from being persisted to the database unless it has a name; it also generates an error message that can be displayed on a page. Additionally, you can write your own custom validations with ActiveRecord.

With that in mind, and after a lot of trial-and-error, research, and asking for help, I finally realized that the best way to ensure that a recipe had at least one ingredient, was to make the name of the first ingredient a required field. This in turn meant that I didn't need to add a #has_at_least_one_ingredient custom validation to my Recipe model (although it's there as an edge case).

As for ensuring that an ingredient had a name, I couldn't just make the Name fields of every ingredient "required", or else the user would have to make at least five ingredients every time. For the same reason, I couldn't add a name validation to the Ingredient model. So, I fiddled around with a lot of (usually overcomplicated) ideas in my models and RecipesController. The solution, as it turned out, was to add this custom ActiveRecord validation to my Recipe model:
```
validate :ingredients_need_names_if_amount_or_brand_are_specified

def ingredients_need_names_if_amount_or_brand_are_specified

    invalid_recipe_ingredient = self.recipe_ingredients.detect do |rec_ingr|
      rec_ingr.ingredient.name.blank? && (!rec_ingr.ingredient_amount.blank? || !rec_ingr.brand_name.blank?)
    end
    
    if invalid_recipe_ingredient
      errors.add(:ingredient, "needs a name when it's given an amount and/or brand")
    end
		
end
```

The validation is called every time a recipe is saved. It looks through a recipe's collection of recipe_ingredients for an invalid one. A recipe_ingredient, as mentioned above, is invalid if it has an amount or brand name, but its corresponding ingredient does not have a name. If the validation finds an invalid recipe_ingredient, then it generates an error message and prevents the recipe from being saved. This ensures that a user can leave an ingredient's name blank *as long as* he/she doesn't specify a corresponding amount or brand. (The only exception is that the first ingredient needs a name because a recipe needs at least one ingredient, as I mentioned earlier.)

[Here is the official documentation for ActiveRecord validations.](https://guides.rubyonrails.org/active_record_validations.html)

## A problem with updating recipes

I encountered yet another problem when trying to update my recipes. Given the validations above, I wanted to update a recipe's recipe_ingredients, but I didn't want to save those updates until I validated and saved the recipe. If I called #update on a recipe_ingredient, that would have changed and saved the recipe_ingredient before the recipe was validated. If the recipe then failed a validation, I would have to somehow revert the changes made to the recipe_ingredient.

The solution seemed simple enough: apply any changes to each recipe_ingredient without saving, then save the recipe. There was just one problem with that: saving the recipe didn't save the recipe_ingredients! I found out that I was trying to do something called "nested attribute updating", which is turned off by default in ActiveRecord. So, I turned on nested attribute updating with this macro in my Recipe model:
```
accepts_nested_attributes_for :recipe_ingredients
```

In retrospect, this was an edge case, since the recipe's validations were already taken care of by the "required" fields in the recipe edit form. However, I have written it here for future reference, as it is one of ActiveRecord's "cracks".

[Here is the documentation for ActiveRecord's #accepts_nested_attributes_for macro.](https://api.rubyonrails.org/classes/ActiveRecord/NestedAttributes/ClassMethods.html)

**Side note:** One thing that I learned while updating recipes is that ActiveRecord has a #find_or_initialize_by method; it works just like #find_or_create_by, except that it calls #new instead of #create. Both methods can be called on a class (such as Ingredient) and a collection of objects (such as recipe.ingredients). Note that when either method is called on a collection of objects, if the method cannot find an existing object from the collection, then it makes a new object and adds it to the collection.

## The art of keeping it simple

I ran into a lot of other problems with my project in addition to what I explained above. However, thanks largely to Jen Pazos from Flatiron, I finally realized that I needed to keep my project simple. Many of my problems were edge cases and/or stretch goals, and others simply weren't worth worrying about. What I had in place with my forms, redirects, and error messages, was good enough for the vast majority of the time; I didn't need to add that much code on top of it.

The problems that I encountered usually boiled down to this: I tried to prevent User A from doing Action B under Condition C. However, at least one of three things was true:
1. Condition C was an edge case; it simply didn't happen very often.
2. User A wouldn't think of doing Action B under Condition C in the first place.
3. Even if User A *did* think of doing Action B under Condition C, that would be impossible to do 90% of the time, unless User A was super computer savvy.

A lot of these problems came up because I had forgotten to come up with an MVP (Minimum Viable Product). Had I done so, that would have helped me simplify my project, and I probably would have completed it in half the time that I did. I will definitely keep this in mind for my other projects. And yes, the irony has not escaped me that I haven't kept this blog post simple either, so I will keep that in mind as well.

## Stretch goals and ideas for more app features

Lastly, I would like to discuss some of the stretch goals that I have for future versions of the Recipe Rolodex. (This might explain why I made it so complicated in the first place.)

First of all, I plan to make this a publicly available web app. Among other things, that means that in addition to CRUD-ing your own recipes, you'll be able to see the recipes that other people have created.

Another stretch goal of mine is to add Javascript to the recipe's "create" and "edit" forms. As I mentioned earlier, users can create up to five ingredients; any additional ingredients go into the Additional Ingredients field. With Javascript, I would give users an "Add Ingredient" option similar to the "Add Education" and "Add Work Experience" options in job applications. Then, users would be able to add as many ingredients as they wanted!

Another thing that I really want to do is allow users to delete ingredients in the recipe's edit form. If they delete the ingredient's information (name, amount, and brand), the ingredient will be removed from their recipe's ingredient list (although not from the ingredients database - the name of the ingredient will still be available in that drop-down list that I mentioned earlier). Most likely, I would use Javascript for this, just as I would for the "Add Ingredient" option above.

Finally, I would like to give credit to Ayana Zaire Cotton from Flatiron for this great idea: Eventually, the Recipe Rolodex could be used by restaurants to crowdsource their recipes. Here's how it would work:
* Restaurants would ask potential customers to submit and vote on recipes that they would like to see on the menu.
* Restaurants could also suggest recipes and food categories of their own.
* Furthermore, restaurants could make a selection of their recipes available to customers with Premium accounts. 
* Those customers could then try out and suggest improvements and variations on those recipes.

I go into more detail about this in the Recipe Rolodex's NOTES.md file. According to [this 2010 article from bon appétit](https://www.bonappetit.com/test-kitchen/article/the-future-of-food-media-food52-and-crowd-sourced-recipes), a company called food52 did something very similar with cookbooks. A quick Google search for "crowdsource recipes" and "restaurants with crowdsourcing" also reveals that crowdsourcing has been done (or at least attempted) by other cookbook companies and by some restaurants.

## Conclusion

This Sinatra project was difficult, but I learned a lot about ActiveRecord's validations, CRUD methods, and what is easy or impossible to do with them. More importantly, I learned (the hard way) about the importance of keeping it simple. I am quite happy with how my Recipe Rolodex turned out, but I have plenty of ideas for future versions.

If you want to check out my project, [here is the link to the Recipe Rolodex's Github repository.](https://github.com/Sdcrouse/recipe-rolodex) You can also [view a demo video here.](https://www.loom.com/share/aae54fd7990e42bd8b6acfb56c71ea33) (My apologies for the cat, though XD )

## Feedback

I am always open to comments and suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.



