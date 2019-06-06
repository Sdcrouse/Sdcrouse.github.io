---
layout: post
title:      "CSS Media Queries from a Rubyist's Perspective, Part 1: The Basics"
date:       2019-06-06 03:22:01 +0000
permalink:  css_media_queries_from_a_rubyists_perspective_part_1_the_basics
---

**Synopsis:** When I read through [Flatiron's "Media Queries" lesson](https://github.com/learn-co-students/media-queries-v-000), I had some trouble understanding the syntax of a media query. More specifically, I wondered how the logic of it works. Media queries are clearly conditional statements in CSS, but which ones are true, and which ones are false? How do operators like "and", "not" and "only" work? I had been working on Ruby in this course for a while, so I was used to seeing conditional statements in the form of "if", "else", "unless", etc. But when I got to the Media Queries lesson, I saw this:

```
@media only screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

Not exactly the same syntax, is it? But then I got to thinking, "Maybe there's a way to write a similar statement in Ruby and understand it better." As it turns out, *there is!* Since I was more familiar with Ruby than media queries, this newly-discovered connection between the two helped me to better understand how media queries work. In this blog post, I'll show you that connection by using the above example and a few others. For this reason, I would recommend reviewing Ruby's logical operators before reading further; [this lesson on Boolean Operators will help with that a lot!](https://github.com/learn-co-students/booleans-ruby-readme-v-000)

Because this blog post is longer than my other posts thus far, I have split it in two. In **Part 1**, I give an overview of @media rules and media queries, and I deal with the basics of their syntax: @media, media types, media features, and the "and" keyword. In **Part 2**, I go *much* more in depth and tackle the parts of the media query syntax that have caused me the most confusion; that is where Ruby has helped me the most.

Happy Reading!

## An Overview of Media Queries

Let's begin with the main purpose of media queries. They are used to change the layout of your website for different-sized devices so that your website looks good and works properly, regardless of whether a user is accessing it with a large desktop or a small cell phone.

Here is a high-level summary of how media queries work: When your website is being accessed by a device that matches the conditions of a media query - say, for example, a media query that targets a mobile phone with a screen width of 375px - the media query will trigger new CSS styles and/or override other CSS styles. Those new CSS styles are geared specifically towards that device (or those devices), and they will *not* apply to anything else that uses your website (unless you use the "all" keyword, which I will discuss in the **Media Types** section). Those conditions (most commonly screen width) that cause the media query to return "true" and change your site's layout, are called "breakpoints". Check out [this article on CSS breakpoints](https://getflywheel.com/layout/css-breakpoints-responsive-design-how-to/) for more information.

One important thing to note is *where* to put your media queries. If you have a small project with a fairly simple CSS file, it's fine to put them in that file as long as they're at the very end of it; that way, the media queries will be able to override the other styles. For larger projects with more complicated CSS, it's a better practice to put your media queries into a separate CSS file; however, there needs to be a `<link>` to that file below the `<link>` s to your other style sheets in each of your HTML files, in order for your media queries to work properly.

## @media and Media Queries

Now, let's look at the @media keyword. @media, and everything after it, is something called a "conditional at-rule". This is what encompasses your media query and its CSS rules. According to [this answer to a Stack Overflow question about nesting @media rules:](https://stackoverflow.com/questions/11746581/nesting-media-rules-in-css/11747166#11747166)
> ...the media query itself is the component that follows the `@media` token, whereas the rule is the entire block of code consisting of `@media`, the media query, and the rules nested within its set of curly braces. 

(Incidentally, "media" refers to the devices using your website; "medium" is the singular for one device.) Written in Ruby pseudo-code, a media query (or more accurately, an @media rule) would look something like this:

```
if (medium/device satisfies this condition)
  # Apply your CSS styles here.
end
```

See [Mozilla's documentation on @media](https://developer.mozilla.org/en-US/docs/Web/CSS/@media) for more information.

## Media Types

In the example that I mentioned in the **Synopsis**, you can see the keyword "screen". "screen" is a *media type*, which refers to the type of device accessing your website. "screen" refers to devices that have screens on them, such as laptops, mobile phones, and tablets. There are three other media types used in media queries today: "print" (pages that are in "Print Preview" mode, for example), "speech" (screen readers and speech synthesizers), and "all" (any and all device types). If you don't specify a media type, then the "all" keyword is implied by default. 

Here's an example of how this would look in Ruby:

```
if media_type == "screen"
  # Apply your CSS styles here.
end
```

See [Mozilla's description of media types](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Media_types) for more information.

## Media Features

Look again at our original example:

```
@media only screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

The part that says `(max-width: 992px)` is a *media feature*. This is the other half of a media query. Here is where you specify the width, height, orientation, etc. that would make your device need different CSS styles than other devices. This is often used to prevent HTML elements on small devices from bumping into each other, but there are plenty of other applications as well. In our case, we are looking at devices with display areas that are no wider than 992px. If we ignore the first half of the media query, it would look something like this in Ruby:

```
if max_width == "992px"
  # Apply your CSS styles here.
end
```

One thing to note here is that `(max-width: 992px)` is *also* equivalent in Ruby to `width <= "992px"` and *not* to `width < "992px"`. In other words, the CSS styles in this media query would apply to devices with a width up to and including *992px* rather than *991px*. 

You can also specify media features *without* providing values. In this case, the media query will return "false" for media features whose values are 0. See [Mozilla's instructions on how to target media features](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Targeting_media_features) for more information.

For example, if you wish to style devices that display in color instead of black-and-white, you can use this @media rule:

```
@media (color) {
  /* Apply your CSS styles here. */
	}
```

The equivalent statement in Ruby would look like this:

```
if color != 0 # Or more accurately, color > 0, since there are no negative color values
  # Apply your CSS styles here.
end
```

(For those who are curious, [Mozilla has more information on the "color" media feature here](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/color).)

## The "and" keyword

Let's look yet again at our example @media rule: 

```
@media only screen and (max-width: 992px) {
  body {
    background-color: blue;
  }
}
```

This time, we'll focus on the "and" keyword. "and" corresponds to Ruby's "&&" operator. In order for the media query above to return true, the device needs to have the "screen" media type *and* be no wider than 992px; if either "screen" or "(max-width: 992px)" is false, the *entire* media query is false, and the CSS rule inside will not be applied. As I will demonstrate in **Part 2** of this blog post, the statement above can be written in Ruby like this, with or without the "only" keyword:

```
if media_type == "screen" && max_width == "992px"
  # Give the document's body a blue background color.
end
```

You can use the "and" keyword to have a media query look for a device with a certain media type and one or more media features (like we did above), or you can have the media query look for a device with multiple media features *without* specifying a media type. However, you can *not* have the "and" keyword separate *multiple media types,* because a device only has *one* media type. (The only exception to this is to write something like `@media all and screen {...}`, but that just shortens to `@media screen {...}` anyway.) See [Mozilla's instructions on how to use the "and" keyword](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Combining_multiple_types_or_features) for more information.

## Conclusion
By now, we know the purpose of media queries, and we have a better idea of the subtle difference between @media rules and media queries. We have also covered a lot of syntax: @media, media types, media features, and the "and" keyword. The one thing we haven't yet covered from our example @media rule is the "only" keyword. I have chosen to save "only" and a few other keywords and logical operators for **Part 2** of this blog post; this is where things started getting *really* confusing for me, and where a good understanding of Ruby's conditional statements came in handy. 

If you're ready to take a deeper dive into the syntax of media queries, read on in **Part 2** (coming soon)! 

## Feedback

I am always open to suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.

## References

1. [Flatiron's "Media Queries" lesson](https://github.com/learn-co-students/media-queries-v-000)
2. [Flatiron's "Boolean Operators" lesson](https://github.com/learn-co-students/booleans-ruby-readme-v-000)
3. ["How to use CSS breakpoints to create responsive designs" (Flywheel article)](https://getflywheel.com/layout/css-breakpoints-responsive-design-how-to/)
4. [@media rules and nesting (Stack Overflow)](https://stackoverflow.com/questions/11746581/nesting-media-rules-in-css/11747166#11747166)
5. [Mozilla's documentation on @media](https://developer.mozilla.org/en-US/docs/Web/CSS/@media)
6. [Mozilla's description of media types](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Media_types)
7. [Mozilla's instructions on how to target media features](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Targeting_media_features)
8. [Mozilla's documentation on the "color" media feature](https://developer.mozilla.org/en-S/docs/Web/CSS/@media/color)
9. [Mozilla's instructions on how to use the "and" keyword](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Combining_multiple_types_or_features)
10. [Mozilla's description of logical operators](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#Logical_operators) 
11. [Mozilla's article "Using Media Queries" (includes many of the above references)](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
