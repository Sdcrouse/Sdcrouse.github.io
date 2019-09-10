---
layout: post
title:      "How to sort by more than one attribute in Ruby"
date:       2019-09-10 22:36:08 +0000
permalink:  how_to_sort_by_more_than_one_attribute_in_ruby
---

I am currently making a Recipe Rolodex app for my Sinatra project. I have my models set up such that a Recipe belongs to a User, and a User has many Recipes. On one page, I decided to list my recipes in alphabetical order, by name. However, I realized that multiple users will likely give their recipes the same name: Scrambled Eggs, for example. Because of that, I want to additionally sort the recipes by their users' names. This is fairly easy to do with a database language like SQL, but how would you do it with Ruby? The answer is surprisingly straightforward...

## The simplest case

Let's start with sorting the recipes by their names. How would you do this? There are multiple ways, but I prefer to use #sort_by:

`recipes.sort_by{ |recipe| recipe.name }`

That produces a list that looks something like this:

```
1. Chicken noodle soup
2. Fruit salad
3. Meatloaf
4. Peanut butter and jelly sandwich
5. Scrambled eggs
```

## A note about #sort and #sort_by

Ruby methods such as #sort and #sort_by use the "spaceship" operator `<=>` behind the scenes. Because of this, words starting with capital letters are higher on the sorted list than all-lowercase words. That could produce unwanted results like this:

```
1. Meatloaf
2. Peanut butter and jelly sandwich
3. chicken noodle soup
4. fruit salad
5. scrambled eggs
```

If you want to sort a list alphabetically, regardless of whether the words are capitalized or lowercased, then append a call to #upcase or #downcase like this:

`recipes.sort_by{ |recipe| recipe.name.downcase}`

That produces a list like this, which is what I'm looking for:

```
1. chicken noodle soup
2. fruit salad
3. Meatloaf
4. Peanut butter and jelly sandwich
5. scrambled eggs
```

## Sorting by multiple attributes

As I mentioned at the start, many users will likely give their recipes the same name; after all, there are multiple ways to scramble an egg, and lots of different ingredients that you can add to it.

Because of this, I want to include the users' usernames alongside each recipe, and sort any duplicate recipe names by the usernames. But how would you do this?

I did a little research, and it turns out that you can still use Ruby's #sort_by method! The syntax just looks a little bit different. When you pass a block to #sort_by, you can put an array inside of it, like this:

```
array.sort_by do |item|
  [item.attribute1, item.attribute2, item.attribute3, etc.]
end
```

That code first sorts the items in the array by attribute1. Any duplicate items then get sorted by attribute2, and then by attribute3, in that order.

In our case, we would sort the recipes like this:

```
recipes.sort_by do |recipe| 
  [recipe.name.downcase, recipe.user.username.downcase]
end
```

That sorts the recipes, first by their names, and then by their users' usernames, which is what we want. Add in a little HTML and ERB syntax, and you get a list like this:

```
1. BAM! 5-minute chicken, posted by elagasse
2. PBJ sandwich, posted by steven.crouse
3. Scrambled eggs, posted by a_flombaum
2. scrambled eggs, posted by g.ramsay
2. Scrambled eggs, posted by Guy_Fieri
3. Zucchini Bread, posted by steven.crouse
```

And there you have it! Sorting by multiple attributes is as simple as ABC.

**Side note:** One thing I just discovered is that numbers and special characters like periods, underscores, ampersands, etc. get sorted higher than lowercase letters, and in an order all their own. Capitalized letters fit somewhere in the middle. So, something like:

`["s4crouse", "s.crouse", "scrouse", "s_crouse", "sCrouse"].sort`

produces this output:

`["s.crouse", "s4crouse", "sCrouse", "s_crouse", "scrouse"]`

Keep this in mind whenever you want to sort a list, especially if it includes usernames and emails.

## Conclusion
So, to wrap up, it's quite easy to sort a list of items with Ruby, even by multiple attributes, once you understand how methods like #sort_by work. Just use `array.sort_by{ |item| item.attribute }` to sort a list by one attribute, and `array.sort_by{ |item| [item.attr1, item.attr2, item.attr3] }` to sort a list by multiple attributes.

Just be sure to watch out for capitalized and lowercased letters, numbers, and special characters.

Thanks for reading through this blog post! I hope it helps you on your coding journey.

**P.S.** For those of you who are curious about how you would do the same thing with SQL, it would look something like this:
```
SELECT recipes.name
FROM recipes
INNER JOIN users
ON recipes.user_id = user.id
ORDER BY recipes.name, users.username;
```

## More information
[How to use sort_by to sort by multiple parameters in Ruby](https://allenan.com/how-to-use-sort_by-to-sort-by-multiple-parameters-in-ruby/)

