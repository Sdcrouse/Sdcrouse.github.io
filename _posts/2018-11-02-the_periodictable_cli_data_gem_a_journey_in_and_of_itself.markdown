---
layout: post
title:      "The PeriodicTable CLI Data Gem: A Journey in and of Itself"
date:       2018-11-02 05:57:28 -0400
permalink:  the_periodictable_cli_data_gem_a_journey_in_and_of_itself
---


Let me be the first to tell you: I tend to overcomplicate things. A. Lot. So, I guess I shouldn't be too surprised that I wound up scraping an entire Periodic Table! Believe it or not, even THIS idea was scaled down from a bigger one. Initially, I had wanted to scrape and recreate a whole BIBLE! But after exploring a few websites, I finally realized that trying to scrape thousands and thousands of verses from 66 books probably wasn't a good idea for my first student project. I may as well have been trying to summit Mt. Everest without ever having climbed up to the top of a 500-foot hill!

From there, I had some trouble figuring out what to scrape, until I remembered watching one of Avi Flombaum's videos that introduced Object Orientation. At one point, he mentioned being able to "model the world around you". As an example, he showed us an Atom class (whose objects were instantiated by sending it a number of protons) and a Compound class (whose objects were instantiated by sending it a collection of Atom objects). I figured, "Hey! Wouldn't it be neat to do just that, but go at it from a scraping angle?" Well, that's exactly what I did...initially.

Here was my idea in a nutshell: I would find a Periodic Table to scrape, then use it to initialize a bunch of different Elements with the properties that I had scraped from that table. Then, I would have the option to list the elements in a specific order depending on which property (name, atomic number, symbol, etc.) was specified. And I could have a collection of Elements, which I could then use to make Molecule objects. ...It didn't take me very long before I realized that while these ideas were good, they were WAY beyond the scope of the project!

After getting some help from the technical coaches with scaling down my idea and choosing the right website to scrape, I finally decided to focus on scraping Wikipedia's List of Chemical Elements page and making Element objects from that data. (I almost wound up scraping Wikipedia's Periodic Table page and the pages of 118 different elements! Thanks for redirecting me, Kenlyn!)

I'm about to go off on a tangent here, so please bear with me. There's a reason why part of the title on this blog post says "A Journey in and of Itself": it's been full of some interesting twists and turns! For instance, when I was about halfway through the project, my dad and I celebrated our birthdays! Then at some point, I discovered while making my coding video that Zoom and other screensharing services are not very compatible with this old laptop of mine. (And by "old", I mean that when I got this thing, the newest version of Microsoft Office was 2007!) Thankfully, I found a service called Loom that works pretty well; I highly recommend it for old laptops and computers in general. (Just be sure to select the "Full Desktop" and "Entire Screen" options, or your audio and video might go out of sync.) 

On top of all that, I learned a few "interesting" things about Nokogiri that you ought to watch out for: 
1. Sometimes, it will have a few extra nodes in its returned collection that you KNOW that you KNOW it shouldn't have put in there! Sometimes, all you're able to do is delete them and move on.
2. Empty node collections will return [] (a blank array) and not "[]", as I learned the hard way.
3. It turns out that Ruby and Nokogiri have two different definitions of what a blank array is, despite the fact that their return values look exactly the same. For example, say that I write something like this in Ruby:

```
if node.children[0] == []
# Do something
end
```

That "Do something" statement never gets executed because the [] expected by Ruby is somehow different than the [] returned by Nokogiri. There is a workaround, however:

```
if node.children[0].size == 0
# Do something
end
```

This works because Ruby is able to recognize when a node collection returned by Nokogiri is empty. That will save you a few headaches, especially if you're scraping a table that contains numerical values. When it comes to programming, that old saying is true: "An ounce of prevention is worth a pound of cure."

Thank you for having the patience to get this far in my blog post! Now, I will finally answer that burning question of yours: What does the PeriodicTable CLI actually DO? Well, one thing it can do is print off a list of the names of 8 or10 chemical elements, or all 118 of them. By default, they are sorted by atomic number - just like in a REAL periodic table! It also gives you the option to sort them alphabetically by their names. My personal favorite part of the program is being able to type in the name of an element; when you do this, the program will list all of the element's properties that it scraped from Wikipedia!

One other thing that I would like to note is that since the elements are as varied as the colors of a rainbow, I decided to let my program reflect that. Let's just say I had a little fun using the Colorize gem...

If you would like to try out the PeriodicTable CLI for yourselves, here is the link to its [Git repository.](https://github.com/Sdcrouse/periodic-table-cli-gem)

If you just want to see my program in action, here is the link to my [walkthrough video.](https://www.useloom.com/share/a51352ba5ccb4f06b11eceeaf403844c)

Overall, this has been a difficult yet worthwhile project. I hope to be able to expand on it in the near future, perhaps in another Learn project! (By the way, if you want to see some more ideas that I have for the PeriodicTable CLI, check out my project's NOTES.md file. Fair warning: it's pretty detailed!) Thanks a lot for reading this, everyone!

#### Feedback

I am always open to suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.

