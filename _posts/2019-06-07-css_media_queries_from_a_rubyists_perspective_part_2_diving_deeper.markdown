---
layout: post
title:      "CSS Media Queries from a Rubyist's Perspective, Part 2: Diving Deeper"
date:       2019-06-07 22:23:15 -0400
permalink:  css_media_queries_from_a_rubyists_perspective_part_2_diving_deeper
---

**Synopsis:** In **Part 1** of this blog post, I took you through the basics of media queries. I also noted that their logic confused me...until I realized that they corresponded to Ruby's conditional statements! As I mentioned at the end of **Part 1**, I will use this second part of my blog post to take you through the parts of media queries that confused me the most - "only", "not", and "," (and their complex interactions) - and where a good understanding of Ruby's conditional statements really came in handy.

I would *highly* recommend reading [Flatiron's lesson on Ruby's boolean operators](https://github.com/learn-co-students/booleans-ruby-readme-v-000) before moving on, if you haven't already. Additionally, here's something to keep in mind as you read through this blog post: even though I have been (and will be) using the terms "@media rule" and "media query" almost interchangeably, they are ***not the same thing.*** As I said in **Part 1**, this is the basic structure of an @media rule:

```
@media [media query] {
  /* CSS styles */
}
```

All that said, are you ready to dive *even deeper* into this thing? OK, here we go...

## The "only" keyword

**---Part A---**

Let's take another look at **Part 1's** example @media rule from [Flatiron's "Media Queries" lesson:](https://github.com/learn-co-students/media-queries-v-000)

```
@media only screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

By now, we at least understand "@media", "screen", "and", and "(max-width: 992px)". But what about the "only" keyword? How does *that* work? Is it even needed? 

Well, for most browsers, the answer is *no*. If we want to change the background color of the document's body to blue, but *only* for screen devices that are no wider than 992px, then this @media rule is perfectly acceptable:

```
@media screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

Obviously, the only difference between this and our original @media rule is the absence of the "only" keyword. So, then, why use "only" at all? Well, it turns out that older browsers need the "only" keyword to do their jobs properly. If they were to see our @media rule without the "only" keyword, they would stop at the word "screen", ignore the rest of the media query, and apply the blue background color to *all* screen devices, not just those with a width of 992px or lower. This is because older browsers don't recognize CSS3 media queries, which are what we've been using so far; they only recognize a list of one or more *media types*. "only" is *not* a media type that they recognize; therefore, if a media query starts with "only", older browsers will interpret it as "false" and not apply the CSS styles. 

Also, be aware that "only" does *not* cause older browsers to use CSS styles inside of @media rules when they *should*; instead, they simply *won't* use the styles when they *shouldn't*. If you want older browsers to use the CSS styles inside of @media rules when they *should,* then you must omit the "only" keyword and use a comma-separated list of media types in your media queries. It is usually better to have a browser not apply *any* CSS styles, than to risk having it apply the *wrong* CSS styles.

That having been said, newer browsers will simply ignore the "only" keyword and move onto the rest of the query. Therefore, to optimize your website's appearance on old and new browsers, it's arguably best to use "only" whenever possible.

Mozilla summarizes all of this in [its section on logical operators](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Logical_operators) and in [its section on improving compatibility with older browsers](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Improving_compatibility_with_older_browsers).

**---Part B---**

This has taken me a while to figure out, but the "only" keyword has ***no*** effect on the truthiness of a media query, other than what I described above. As far as I can tell, Ruby doesn't have a corresponding keyword or logical operator, either.

Incidentally, it is perfectly acceptable most of the time to write an @media rule whose media query only has a media type or a media feature specified. `@media screen {...}` and `@media (max-width: 992px) {...}` are both legal @media rules; the latter is equivalent to `@media all and (max-width: 992px) {...}`. However, when you use the "only" keyword, *you must specify a media type!* `@media only screen {...}` is acceptable, but `@media only (max-width: 992px) {...}` is *not*. See [this answer to a Stack Overflow question about "only"](https://stackoverflow.com/questions/8549529/what-is-the-difference-between-screen-and-only-screen-in-media-queries/14168210#14168210) for more information.

> **Side note:** This is pure speculation, but it occurs to me that all of the code in a CSS file can be implicitly wrapped up inside of an @media rule like this:
> 
> ```
> @media all {
>   /* All CSS styles and media queries go here. */
> }
> ```
> 
> Mind-blowing, isn't it? (And as you might have guessed from above and/or [this resource from Part 1 of my blog post](https://stackoverflow.com/questions/11746581/nesting-media-rules-in-css/11747166#11747166), it *is* possible to nest media queries; however, that is a topic reserved for another time.)

Moving right along, we now know that our example @media rule applies to screen devices that are 992px wide or thinner, like tablets and cell phones. But what if we wanted to do something like styling every device *except* screen devices with landscape orientations? Read on...

## The "not" operator

**---Part A---**

This is where it gets more fun (sarcasm intended). Let's start by answering that question from the end of the previous section. To style every device *except* screen devices with landscape orientations, you would write this:

```
@media not screen and (orientation: landscape) {
  /* Apply your CSS styles here. */
}
```

Hold up. That doesn't look right! Isn't that media query *really* checking for devices that don't have a "screen" media type but *do* have a landscape orientation? In other words, isn't *this* really what our media query's logic would look like in Ruby?

```
if device != "screen" && orientation == "landscape"
  # Apply your CSS styles here.
end
```

That was my line of thinking at first, but it turned out that I was wrong! Written in pseudo-code, my media query is *really* implying this: `not ( screen and (orientation: landscape) )`. In other words, the "not" operator is cancelling the *entire* media query, not just the "screen" media type! Therefore, it would look like *this* in Ruby:

```
if !( device == "screen" && orientation == "landscape" )
  # Apply your CSS styles here.
end
```

This is arguably a clearer way to write it:

```
unless device == "screen" && orientation == "landscape"
  # Apply your CSS styles here. (In case you're tired of seeing that sentence everywhere, I'll use something else soon.)
end
```

Now we can see that our @media rule:

```
@media not screen and (orientation: landscape) {
  /* Apply your CSS styles here. */
}
```

styles every device *except* screen devices with landscape orientations, just like we wanted!

**---Part B---**

Just like with the "only" keyword, *you must specify a media type with the "not" operator*. For example, if you wanted to change the text color to red in every device *except* those with widths of at least 800px, this @media rule's syntax would *not* work:

```
@media not (min-width: 800px) {
  body {
	color: red; /* There we go! Something different at long last! */
  }
}
```

Instead, you would have to use the "all" media type in your media query, like so:

```
@media not all and (min-width: 800px) {
  body {
	color: red;
  }
}
```

Just to prove that this works, remember that this is equivalent in Ruby to:

```
unless device == "all" && min_width == "800px"
  body_text_color = "red"
end
```

Since *every* device falls under the "all" media type, the first part of that conditional statement is *always true;* the *entire* conditional statement will only ever return "true" if the *second part* is true as well. Thus, the text color on every device will change to red *unless* its width is at least 800px, which is what we wanted.

Check out these resources for more information:

* [Mozilla's description of logical operators](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Logical_operators) 
* [Mozilla's section on how to invert a media query's meaning](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Inverting_a_query's_meaning)

## The "," operator and complex media queries

**---Part A---**

This part is where I struggled the most with the logic of media queries. To begin, suppose you wanted to split the paragraphs on your website into two columns, but only if your device's orientation is landscape, or if you're using a tablet or computer whose screen is at least 800px wide. In that case, you have a couple of options. You could write two separate @media rules like this:

```
@media (orientation: landscape) {
  p { 
	  -webkit-column-count: 2; /* Chrome, Safari, Opera */
    -moz-column-count: 2; /* Firefox */
    column-count: 2;
  }
}

@media only screen and (min-width: 800px) {
  p { 
	  -webkit-column-count: 2; /* Chrome, Safari, Opera */
    -moz-column-count: 2; /* Firefox */
    column-count: 2;
  }
}
```

If you'll notice, though, that's not very DRY; you have *six lines of repeating code!* Thankfully, though, you can easily shorten it with the "," (comma) operator! Instead of writing all that code above, you can write this instead:

```
@media only screen and (min-width: 800px), (orientation: landscape) {
  p { 
	  -webkit-column-count: 2; /* Chrome, Safari, Opera */
    -moz-column-count: 2; /* Firefox */
    column-count: 2;
  }
}
```

The reason why this works is that the "," operator corresponds to Ruby's "||" (or) operator. Thus, our @media rule above can be written in Ruby like this:

```
if (device == "screen" && min_width == "800px") || (orientation == "landscape")
  paragraph_column_count = 2
end
```

That's *also* why we can use a comma-separated list of media types for older browsers, like we discussed in **Part 1**. (By the way, if you'd like more information about the column-count property, check out [this W3Schools article](https://www.w3schools.com/cssref/css3_pr_column-count.asp).)

**---Part B---**

Note that because of the nature of the "only" keyword mentioned earlier, you only need to use it at the *start* of an @media rule. It's not necessary to use it in *each* media query in a comma-separated list.

**Don't write this:**

```
@media only screen and (max-width: 700px), only screen and (orientation: landscape) {
  p {
	  font-size: 2em;
  }
}
```

**Write *this* instead:**

```
@media only screen and (max-width: 700px), screen and (orientation: landscape) {
  p {
	  font-size: 2em;
   }
}
```

However, this is *not* the case with the "not" operator; "not" cancels out *one* media query, not the *entire list!* Therefore, in a list of comma-separated media queries, you have to apply "not" to *each* media query that you want to cancel out.

Take a look at these comma-separated media queries:

```
not screen and (min-width: 500px), print and (orientation: portrait)
```

In this case, the "not" operator just cancels out the `screen and (min-width: 500px)` media query; it does *not* cancel out the `print and (orientation: portrait)` media query. If you want the "not" operator to cancel out *both* media queries, then you have to write this:

```
not screen and (min-width: 500px), not print and (orientation: portrait)
```

Check out these resources for more information:
* [Mozilla's description of logical operators (again)](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Logical_operators)
* [Mozilla's section on creating complex media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Creating_complex_media_queries) 

## Conclusion

If you got to the end of this *long* two-part blog post (and your mind isn't overloaded with information), bravo! Don't worry, though; I intend to make my next blog post much shorter and easier to read. That said, I hope that this has given you a better idea of how media queries work, and how their logic works a lot like Ruby's conditional statements. If you've gotten confused by any of the keywords, code, logic, etc, don't worry. It wasn't easy for me either, but the logic *is there;* it just takes time, practice, and patience to understand.

For the record, if anybody is wondering, it *is* possible to simplify your media queries. You can do this with Level 4 syntax, nested media queries (as I noted at the end of the **"only" keyword** section), and other methods. However, that topic is best reserved for another blog post. *But* for those who are curious and are ready to go down *another* rabbit hole, check out the **Additional Resources**.

Peace be with you all.

## Feedback

I am always open to comments and suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.

## References

1. [Flatiron's "Boolean Operators" lesson](https://github.com/learn-co-students/booleans-ruby-readme-v-000)
2. [Flatiron's "Media Queries" lesson](https://github.com/learn-co-students/media-queries-v-000)
3. [Mozilla's section on logical operators](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Logical_operators) 
4. [Mozilla's section on improving compatibility with older browsers](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Improving_compatibility_with_older_browsers)
5. [How to use the "only" keyword (Stack Overflow)](https://stackoverflow.com/questions/8549529/what-is-the-difference-between-screen-and-only-screen-in-media-queries/14168210#14168210)
6. [@media rules and nesting (Stack Overflow)](https://stackoverflow.com/questions/11746581/nesting-media-rules-in-css/11747166#11747166)
7. [Mozilla's instructions on how to invert a media query's meaning](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Inverting_a_query's_meaning)
8. [CSS column-count property (W3Schools)](https://www.w3schools.com/cssref/css3_pr_column-count.asp)
9. [Mozilla's section on creating complex media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Creating_complex_media_queries) 

## Additional Resources
* [Mozilla's article "Using Media Queries" (which includes many of these references and resources)](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
* ["Logic in Media Queries" (CSS Tricks article)](https://css-tricks.com/logic-in-media-queries/)
* [Mozilla's documentation of syntax improvements in Level 4](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Syntax_improvements_in_Level_4)
* [W3C’s documentation of Level 4 media queries](https://www.w3.org/TR/mediaqueries-4/)
* [W3C's documentation of Level 4 media features](https://www.w3.org/TR/mediaqueries-4/#mq-features)
