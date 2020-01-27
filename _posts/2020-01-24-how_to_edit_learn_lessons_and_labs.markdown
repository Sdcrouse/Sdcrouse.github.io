---
layout: post
title:      "How to Edit Learn Lessons and Labs"
date:       2020-01-24 20:02:39 -0500
permalink:  how_to_edit_learn_lessons_and_labs
---

**Introduction:** Have you ever worked on a lesson or a lab, only to realize that it didn't look quite right - like maybe it had a couple of incorrect instructions, a sentence or two that could be phrased more clearly, or even a missing test? It happens. The people who write Learn's curriculum are (just like the rest of us) imperfect; as such, there are going to be a few problems with the lessons here and there. But how do you fix them? You could Raise an Issue, but that might take a while to get fixed, depending on how urgent the issue is and/or how easy it is to solve. Thankfully, there's another, arguably better option: opening a pull request on the lesson/lab itself! In this post, I'll show you how to do just that (*Hint: Just treat it like any other repository*).

## Open up the lesson's GitHub repository

Let's use the **Basic Nested Forms** lab as our example. Suppose we wanted to add a Summary at the top:

<img src="https://doc-00-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/5opv78o5gqrqd7al8os6d0616dahjhjo/1580090400000/18375684649449857957/18375684649449857957/1X5XbRKigohSp2fhcWIMJ3QD3gJuyGXiU?e=view&authuser=0" alt="Lab with Summary Suggestion at Top" />

The first thing we need to do is get to the lab's GitHub repository. You might be thinking, "OK. I'll just click on the **Open in Github** icon at the top of the lab." However, as I've been told, that usually takes you to the *wrong repository*. What you need to do is find the lesson at

```
https://github.com/learn-co-curriculum/[your-lesson-name]
```

I've found that the easiest way to do this is to click on the **Raise an Issue** icon at the top of the lesson:

<img src="https://doc-0c-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/jb2lm6jv3sjjasgti2888003egioffik/1580090400000/18375684649449857957/18375684649449857957/1gRkku9VTNIV4jzDa0gcU-qGnlPA38NsU?e=view&authuser=0" alt="Raise an Issue icon" />

This will take you to the correct repository:

<img src="https://doc-0c-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/fr1sp1mjlu0a11k32c9i5i27njrqp0jb/1580090400000/18375684649449857957/18375684649449857957/1YF3b4D3EVYPigOrwUX5SbCztpIwcs4fl?e=view&authuser=0" alt="Learn Lab Repository" />

> **Side Note:** This only applies to labs and codealongs, which have a blue **Open IDE** icon at the top. For regular lessons, which have a blue **Sandbox** icon, you can click on the **Open in Github** icon or the **Raise an Issue** icon; either one will take you to the correct repository.

## Fork the lesson

> **Side Note:** These next few steps are a review of forking, cloning, editing, committing your changes, and pushing to Github. If you want to skip all of that, go to the **"Review your changes on GitHub"** section.

Click the **Fork** button in the top right corner:

<img src="https://doc-04-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/066bo88agvrl11bj0e8hdg2tgdlb8ll2/1580090400000/18375684649449857957/18375684649449857957/1DpSIiYy4ct985H9_7zldzAwlg3ZFo--j?e=view&authuser=0" alt="Fork Button"  />

You should then see a pop-up window:

<img src="https://doc-08-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/5bovpm8guff90lrtgupvncjlo9rkictv/1580090400000/18375684649449857957/18375684649449857957/1bVkF2C6eLPq2dGVGo7XX1UKXw3r4RJ1a?e=view&authuser=0" alt="Pop-Up Window for Fork Button" width="400" height="304" />

Just click on your profile icon and name, and wait a few seconds to be redirected to your newly forked repository. (If you've forked this repository before, the pop-up window will look a little different from the one above; just click on the link that it shows you, and you'll be redirected to your fork). You should see something like this: 

<img src="https://doc-0g-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/n1l0pe333gbafcacfia9fpr2sbrvtfll/1580090400000/18375684649449857957/18375684649449857957/1TZUqzZLBqqdPQTuedhRXgvnqVhx3gApG?e=view&authuser=0" alt="Fork of Lab Repository" />

## Clone the lesson into your IDE or local environment

Click the **Clone or download** button in the top-right corner, then click the clipboard icon in the pop-up window (I use SSH, but you can use HTTPS if you'd prefer):

<img src="https://doc-10-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/ap387gknj051lr25e76va3q1mff623k6/1580090400000/18375684649449857957/18375684649449857957/1ws_TJViUo9AZa_GAjmeYVL5HF4yPND0E?e=view&authuser=0" alt="Clone or Download Button and Pop-Up" />

Now, go to your IDE or local environment, and write `git clone [paste-your-repo-name-here]`. The repo-name is what you copied from Github when you hit the clipboard icon. Now, `cd` into that new directory. I'm using VSCode in this case, but your command terminal should look something like this:

<img src="https://doc-08-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/cuqom8ovqb85sr0kd06o6k944kmpo867/1580090400000/18375684649449857957/18375684649449857957/1FBe7wOmD38-a24OodyNQIJT9sWSMWDFI?e=view&authuser=0" alt="Command terminal with 'git clone' and 'cd' commands" width="568" height="240" />

## Make your changes to the lesson or lab

Let's add a Summary to this lab's README.md file:

<img src="https://doc-0k-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/07gjbofmh3bd9888lc9io704rqt2n73g/1580090400000/18375684649449857957/18375684649449857957/1XZrQhlqKVKknNSnlNrDTLZfpjFGkV0Sb?e=view&authuser=0" alt="Summary added to lab Readme" />

> **Side note:** If you make any changes to a lab's test suite, be sure to try them out on your original lab first. Make sure the tests still work!

That all looks good, so we can move onto the next step.

## Add, commit, and push your changes

Let's stage our changes with `git add .` and commit them with `git commit -m "Your commit message here"`:

<img src="https://doc-0c-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/v0i43k6jcescm9jnqh0brtsbp550ucba/1580090400000/18375684649449857957/18375684649449857957/1ROesM-KfIhXEf8rbk8-qxHUH3OWfq_eq?e=view&authuser=0" alt="Adding and committing changes" />

If you want to add a description to your commit that explains your changes in more detail, just write `git commit`. That will open up a text editor. You'll be able to write and save something like this (I'm using "GNU nano", but you can use whatever text editor you want):

<img src="https://doc-08-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/hjuvq8oach7anabspm409nn994g2us6v/1580090400000/18375684649449857957/18375684649449857957/1q0hRUbzSS0WnoHuLnuBsHZPc3OZ94XYW?e=view&authuser=0" alt="Git commit message and description on GNU nano" width="600" height="250" />

Finally, push your changes back to your repository with `git push`: 

<img src="https://doc-0o-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/ln81u8672q18ur3pqg92d1tvophpeoqn/1580090400000/18375684649449857957/18375684649449857957/1Ygi4moKXQMJSk1Dya_xG1akSl_hG5Dns?e=view&authuser=0" alt="Using Git Push" width="600" height="256" />

## Review your changes on GitHub

Go back to your GitHub repository and refresh it. If you pushed your changes successfully, your repository will show your last commit, and it will be at least one commit ahead of the original lab's repository:

<img src="https://doc-00-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/jrb8818mrsvo33v7b4rf3t8bbcnjfiqc/1580090400000/18375684649449857957/18375684649449857957/1ousuePxUlfWTNw6m6nbfrXMJsJ_is1gs?e=view&authuser=0" alt="GitHub repository with latest commit" width="706" height="375" />

Since we changed the README.md file, we can see our changes by scrolling down:

<img src="https://doc-0o-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/09v9v8ddlnd4tgg2735nmc47q3h5i1kj/1580090400000/18375684649449857957/18375684649449857957/1vRuwSkcvRra7hs59Vom_SuwRJmbTIlNH?e=view&authuser=0" alt="Changes to Readme.md file" width="681" height="250" />

That looks good, so let's move onto the next step. If you want to change something else, then add, commit, and push your changes before coming back here.

## Open a Pull Request

We are finally ready to make a pull request! To do this, click on the **New pull request** button:

<img src="https://doc-0g-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/ic5livkubjnqafomuia4kb2pval2qaak/1580090400000/18375684649449857957/18375684649449857957/1gy0QkaB3CEAorgBeFJUXIq_8m57VoWqr?e=view&authuser=0" alt="New pull request button" width="600" height="387" />

If your commits can be merged into the lab's repository, you'll be taken to the **Comparing changes** page with a green **Create pull request** button. It will look something like this:

<img src="https://doc-0c-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/015kkmk5emveam0b07sq595ln0s45hej/1580090400000/18375684649449857957/18375684649449857957/1Y4C7c_cFo0Jqr6SeKU67pvqpKZ7EMj4w?e=view&authuser=0" alt="Screen with 'Create Pull Request' button" />

When you click on that button, you'll be taken to the **Open a pull request** page. Here, you can review your commit and edit your commit message and description. Click the **Create pull request** button, and you're done!

<img src="https://doc-04-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/t55fdltdol8jqdvmhugld89lkosff8ej/1580090400000/18375684649449857957/18375684649449857957/131Ib6lAlppfoOBjpN1uYDh7lSLLseYsT?e=view&authuser=0" alt="Open a pull request" />

> **Side note:** Since this is just an example, I won't actually submit the pull request. The last thing I want to do is create a major headache for the Learn team!

If you're being *really* awesome by solving a raised issue with this pull request, go ahead and edit your commit description in the **Write** tab. Write something like "Fixes issue..." and paste in the URL of the raised issue. After you hit **Create pull request**, this will create a link to the raised issue on the pull request's page. (**Note:** I'm using a different example here, with an already-merged pull request for a closed issue.)

<img src="https://doc-10-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/l46qkdbf8cvv6nsdd67ai506qmjk43gd/1580090400000/18375684649449857957/18375684649449857957/13i0XWaXaQ7JgqrhA1NN3Xiweu_cbUbKk?e=view&authuser=0" alt="Merged pull request referencing closed issue" />

It will also create a link to the pull request on the raised issue's page:

<img src="https://doc-08-cc-docs.googleusercontent.com/docs/securesc/ko5vot4vvg9f2tjfpgn08k3am7vsnadp/af44qrscmsqggveh0lfqqi27fd3gm8e5/1580090400000/18375684649449857957/18375684649449857957/1YG6tjEdJACqPoT2eQ1SnsCVOq7yJuPDb?e=view&authuser=0" alt="Closed issue referenced by merged pull request" />

Cool! There's just *one* more thing that we may need to do.

## Make additional commits as needed

Suppose that you made a mistake with your pull request, or you've realized that you forgot to make an important change. What do you do, open another pull request? Thankfully, the answer is no. Just make a new commit, and push it to GitHub. That commit will be added to your pull request *automatically*.

**That's it!** Now you can make changes to any lesson/lab that you want! (But please make *good* changes; be nice to the Learn team.)

## Hold up! Why would you want to do all of this in the first place? Why not just Raise an Issue?

To be fair, if you don't know how to solve the problem, it's probably better to Raise an Issue. However, if you *can* solve the issue with a pull request, then I *highly encourage it*. Here are a few reasons why:

1. It benefits the *Learn team* a great deal! It's much easier (and quicker) for them to merge in an existing pull request, than to read over an issue, familiarize themselves with it, figure out how to solve it, make the needed changes, and merge them in.
2. It benefits *other students*. The quicker that the lesson/lab is fixed, the less likely other students will have the same problem that you had. And for those students who *have* had the same problem, they'll be able to look back at the lesson and see that it's been fixed! This is especially true if your pull request fixes an issue that they raised.
3. It benefits *you*. For one thing, you'll get experience with fixing a real-world problem, and you'll get to practice using Git and GitHub, both of which are skills that a lot of web development jobs (among others) are looking for. And - let's face it - you'll feel good doing it! "Virtue is its own reward", after all, and you'll get to say that you contributed to the Learn curriculum.

So, you'll wind up helping out a lot of people just by submitting a pull request. Why not give it a shot?

## More Information

[Pull request basics](https://github.com/learn-co-curriculum/github-pull-request-basics)
[How to make a commit with a message and description](https://stackoverflow.com/questions/16122234/how-to-commit-a-change-with-both-message-and-description-from-the-command-li)

## Feedback

I am always open to comments and suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.
