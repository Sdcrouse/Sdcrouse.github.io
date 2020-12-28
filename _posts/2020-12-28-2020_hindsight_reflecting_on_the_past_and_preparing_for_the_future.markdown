---
layout: post
title:      "2020 Hindsight: Reflecting on the Past and Preparing for the Future"
date:       2020-12-28 02:44:05 -0500
permalink:  2020_hindsight_reflecting_on_the_past_and_preparing_for_the_future
---

Happy Holidays, everyone! First of all, I must again apologize to those who were expecting Part 3 of my React/Redux blog post series. I finally realized that I needed help with understanding `useSelector`, Reselect, memoization, etc. As such, I won't be able to write Part 3 until the end of the week/year. In the meantime, since the end of 2020 is quickly approaching, I have decided to do a little reflection on what I've learned and what I want to do going forward. Here are five lessons I learned in 2020, and five goals for 2021.

## 5 Lessons Learned in 2020

### 1. Think carefully before refactoring your React project with hooks.

As I mentioned in previous blog posts, I decided to gain experience with React hooks by using them to refactor my React/Redux project. I succeeded with this, but not without learning the hard way that some React class components are easier to refactor into functional components than others. It can be a real headache, even if you know what you're doing! For future reference, if you want to practice using React hooks, I would advise you to do one of two things:

1. Create new components with hooks instead of refactoring old ones, or
2. Refactor your components with hooks if these components are very simple or if you *absolutely* need to make your code more readable and/or improve performance. Otherwise, don't bother.

### 2. Keep your projects as simple as possible when you first create them.

This is easier said than done, I'll admit. It's extremely easy to overcomplicate your project, only to realize that (time and effort-wise) you've bitten off more than you can chew! What you'll want to do is come up with a few simple requirements - maybe three user stories, for starters - and build your project from there. Keep an MVP (Minimum Viable Product) in mind at all times. Later on, you can add on more features as you see fit. If you approach new projects with this mindset, you'll save yourself a lot of time and stress.

### 3. Bugs, while tricky, can be a great learning experience.

As an example, when I worked on my JavaScript project, I found a bug with one of my event listeners. I wrote a blog post that goes into more detail about it (see [Reference 1](https://stevendcrouse.com/how_i_fixed_a_tricky_event_listener_bug_in_my_project)), but here's the gist of it: The main page loaded a form by default, and it had a button to generate a new form. The default form submitted just fine, but the button-generated form did *not*.

Originally, I had used the same event listener for submitting the default form and the button-generated form because they had the same HTML. What I hadn't realized was that even though the HTML for the forms was the same, they were in fact two separate forms, each requiring their own separate event listener. I fixed this and later learned how to refactor my solution, while learning about event delegation in the process.

This bug wasn't fun to solve, but I learned a lot about how JavaScript works in the process. Debugging can be frustrating, but more often than not it's a great learning opportunity!

### 4. Connect with people often, especially in these crazy times.

I'm consistently blown away by who I meet online, especially through LinkedIn. For example, I had connected with a fellow university graduate years ago. Fast forward to 2020, and I decided on a hunch to ask her about working as a software engineer. That wound up turning into a fun and insightful conversation, which then led to me speaking with a technical recruiter at her company! I've stayed in contact with her since, and I'll be talking with her this week about my React/Redux project. The fact that one of my church friends knows people on her team is just icing on the cake!

Another example: While writing this blog post, I connected with someone who works at my church, and who happens to know a couple of friends of mine in the IT field. I look forward to seeing what happens next!

You just never know who knows whom, or what kind of wonderful conversations you'll have just by reaching out. You may find yourself having some much-needed social interaction during this global quarantine, too. I never fully realized the value of socializing, until I was forced to limit it. I can't say it enough: Connect and stay connected with people!

### 5. When planning your web projects, wireframe them first.

Wireframing can be a little awkward at first, especially if you're learning how to do it online with Figma or Adobe XD. But what I discovered is that once you wireframe your projects, you have an excellent visual goal to work towards. It's like assembling a jigsaw puzzle: Having all of the pieces (i.e. user stories, backend, overall goal, etc.) is good, but having a picture of the finished puzzle to reference (i.e. the wireframe) makes it much easier to assemble the puzzle/app. It gives you something to reference. You can technically create an app without a wireframe, but it becomes much harder to visualize the end product that you're working towards.

There are also some companies out there that look for experience with wireframing tools such as Figma and Adobe XD, so it definitely can't hurt to learn how to use them.

## 5 Goals for 2021

### 1. Learn Python, Java, and C# or C++ and some of their corresponding frameworks

I've been at the job search for a couple of months now. From what I can tell, a lot of companies are looking for people who have experience in at least one of these languages.

Python, like Ruby, is an easy-to-learn and very readable programming language. It's high-level and widely used by companies such as Google, Amazon, and Facebook. It also has a wide range of uses, such as web development, machine learning, and scraping. A popular Python web framework is Django, which is used by YouTube, Instagram, Dropbox, and other companies. Check out [Reference 2](https://www.geeksforgeeks.org/python-programming-language/?ref=lbp) for more information.

Java was created in 1995, and it's still widely used today. It is open source and used for mobile, desktop, and web applications, just to name a few (see [Reference 3](https://www.w3schools.com/java/java_intro.asp)). Frameworks that use Java include Spring, Hibernate, and Google Web Toolkit, among others (see [Reference 4](https://www.edureka.co/blog/java-frameworks/)).

(C# is an object-oriented language used by Microsoft in many of its .NET apps. C# runs on the .NET framework, which also supports the F# and Visual Basic languages (see [Reference 5](https://docs.microsoft.com/en-us/dotnet/csharp/getting-started/) and [Reference 6](https://docs.microsoft.com/en-us/dotnet/core/introduction)).

Finally, C++ is "a powerful general-purpose programming language [that] can be used to develop operating systems, browsers, games, and so on" ([Reference 7](https://www.programiz.com/cpp-programming)). For a list of handy C++ frameworks and libraries, check out [Reference 8](https://github.com/fffaraz/awesome-cpp#frameworks).

### 2. Create a portfolio website

This is a goal that I intend to accomplish as soon as possible. From what I've learned at Flatiron so far, a portfolio website is a great way to showcase my projects, blog, and resume all in one place. Once I deploy my projects, I can provide links directly to them instead of to their GitHub repositories. This would let me not only demonstrate my programming skills, but it would also give employers a visual of who I am and what my interests are. The greatest part: I can have fun with it and make it look however I want!

### 3. Deploy my apps

Once I finish refactoring my projects, I want to deploy at least a few of them. Based on a few recommendations I've received, I will probably deploy the backends of my projects to Heroku and the frontends to Netlify or something similar. The reason I want to do this, as I touched upon in the previous goal, is that I want to be able to provide links in my portfolio to fully up-and-running apps, rather than links to their GitHub profiles. From a user's perspective, it's tedious to fork and clone a project and follow the README's installation instructions just to start the app. I'd rather the app be easy to access and start up, from the get go.

### 4. Start a brand new project

Flatiron has done a great job of helping me with developing some fun projects along the way. However, each of these projects had their own sets of requirements in place, so my options were limited in some ways. As I mentioned in my first goal, I want to branch out and learn new languages and frameworks. My hope is that I can then apply what I learn towards a new project that makes use of at least one new language and framework. 

I could also create a project that makes use of the languages and frameworks that I know, but in ways that I haven't tried before (for example, a puzzle app that utilizes JavaScript and the HTML `<canvas>` element). Either way, the idea here is to show employers (and myself) that I am capable of learning and applying new technologies quickly and effectively, and that I can create and manage new projects from start to finish.

### 5. Complete the requirements for the Career Services Commitment until I get a junior-level developer role

While it's good to keep up with the Career Services Commitment as much as possible, I am ultimately more interested in obtaining a job than in Flatiron's Money-Back Guarantee. That was the reason I attended Flatiron in the first place - to switch careers into web development! As such, I will network, learn, code, and write blog posts until I am hired for a junior web developer/software engineering role.

Once I get hired, I won't stop networking, learning, or blogging. It's a good idea to keep learning and stay up-to-date on technology. Maintaining and nurturing my network will also help my career a lot, and it's just a good thing to do in general; as I mentioned earlier, you never know who you'll be able to help or receive help from in the process!

Depending on where I work, I may also get AWS Certification and/or learn about microservices and Docker, just to toss out a few ideas. That's more of a long-term goal, but I may wind up attaining it after I get a job. I'll just have to see where my journey takes me!

## Conclusion

2020 has been quite a year! For better or worse, it limited me in some ways, while benefitting me in others. Yes, it stinks being socially isolated for this long, but I've learned to adapt. And I've learned a lot of great programming and life lessons along the way. To paraphrase Charles Dickens, it's been the best of years, it's been the worst of years.

My overall goal for 2021 is to become a junior web developer/software engineer, and to never stop learning. To that end, once COVID is over, I'll be interacting with people in person as much as possible - if not for the sake of my career, then for the sake of my sanity! I also have a bonus goal: to complete Part 3 of my React/Redux series before the year is over; thanks for your patience, readers.

Have a Happy New Year, everyone! Take care, and God Bless.

## References

1. [How I Fixed a Tricky Event Listener Bug in my Project](https://stevendcrouse.com/how_i_fixed_a_tricky_event_listener_bug_in_my_project)
2. [Introduction to Python](https://www.geeksforgeeks.org/python-programming-language/?ref=lbp)
3. [W3 Schools Java Introduction](https://www.w3schools.com/java/java_intro.asp)
4. [Top 10 Java Frameworks](https://www.edureka.co/blog/java-frameworks/)
5. [Introduction to the C# language and .NET](https://docs.microsoft.com/en-us/dotnet/csharp/getting-started/)
6. [Introduction to .NET](https://docs.microsoft.com/en-us/dotnet/core/introduction)
7. [Learn C++ Programming](https://www.programiz.com/cpp-programming)
8. [C++ Frameworks](https://github.com/fffaraz/awesome-cpp#frameworks)
