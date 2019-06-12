---
layout: post
title:      "Route vs. Controller vs. Path vs...Everything Else"
date:       2019-06-12 23:12:30 +0000
permalink:  route_vs_controller_vs_path_vs_everything_else
---


**Synopsis:** After completing a lesson about routes, I was still confused about what a route *was* and what it was *not*. After getting some help from some great Technical Coaches (thanks, Madeline and Isaac!), I believe I have a better grasp on it. My hope is that my explanation here will clarify a few concepts and be useful for future reference. It will also cover most of the MVC and "request/response cycle" concepts, but it won't go into too much detail. (I went into more detail about the request/response cycle in a previous blog post; I might make an MVC post later.) And as I promised, I will make this post *much* shorter than my previous ones.

## The Controller

To start off, let's say that somebody using our application types in this URL: `https://localhost:9393/medicines`. Now let's say that we have the following code inside of our medicines_controller.rb file:

```
class App < Sinatra::Base

  get '/medicines’ do
    #Get data and make a response.
  end
	
end
```

## Deconstructing the Controller

Here are the pieces of the puzzle (in addition to the URL above):

* The App class is the **controller** that inherits from Sinatra::Base.
* `'/medicines'`is the **path** or **resource** that the user has requested.
* `get '/medicines'` is the **route**.
* The entire `get '/medicines' do {...}` code is the **controller action** or **action block**. However, the **controller action** can also refer to what the code is *doing*, as I will explain below. 

Note that the **route** and **controller action** somewhat overlap, which is why the terminology can get confusing.

## Putting It Together

From what I understand, this is how the pieces of the puzzle fit together:

1. The user types in a URL that has the "/medicines" path/resource (`https://localhost:9393/medicines`).
2. The browser makes an HTTP GET request with that URL and sends it to the App controller, thanks to the the Sinatra framework and a few other pieces of software and hardware.
3. The App controller receives the request and matches it to the `get '/medicines'` route.
4. Then, the App controller makes the appropriate response with the `get '/medicines' do {...}` controller action/block.
5. Again, the entire process of the controller receiving the request, matching it to the route (if possible), and creating and sending a response is *also* called the "controller action".

## Exploring the Controller Action

Let's also get a little more specific about how the `get '/medicines' do {...}` controller action/block works:

1. It sends `‘/medicines’` as an argument to the #get method, along with a block. It can also look like this: `get ('/medicines') {some code}`.
2. Within the block, the controller retrieves the relevant data from our Model file(s), sends the data to our View file(s) to create an HTML response, and sends the response back to the browser, where it is rendered.
3. If the controller can't match the path to a route, it sends back a 404 error.

There are also pieces of hardware like routers and modems that are connected to all of this, but that is a different (though related) subject. However, for those who are curious, routers are discussed in [this Lifewire article](https://www.lifewire.com/what-is-a-router-2618162).

## Conclusion

As far as I can tell, this is how it all works. If need be, however, I will update this later with more accurate information. I hope that this has clarified a few concepts for you, especially with regards to what a route is (and what it is *not*).

As always, peace be with you!

## Feedback

I am always open to comments and suggestions for improvement on my blog posts! If you have any feedback for me, please feel free to [raise an issue here](https://github.com/Sdcrouse/Sdcrouse.github.io). I will do my best to get back to you promptly.
