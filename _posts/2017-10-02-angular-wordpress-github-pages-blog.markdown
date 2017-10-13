---
layout: post
title:  "Angular, Wordpress & Github Pages blog"
date:   2017-10-13 13:00:00 +0200
---

Hello.

I have recently created my personal website and started writing a blog. The first version of it was written in Angular and used Wordpress for the backend. Why? I don't really know, just wanted to play around with Angular while learning it and test Wordpress REST API. Now I switched to Jekyll, because it's much simplier and is fitting better for creating a blog, but integrating Angular, Wordpress and Github Pages was pretty educative experience.

You can check out all the code of this project on [Github](https://github.com/oskar1233/awg-blog) and working example [here](https://awg.oskar1233.eu). I probably won't continue to develop it, but if you have similar mad idea feel free to use it on your purpose. And under your responsibility.

# Overview

The website has working posts index and single post view. It's fetching data from my test Wordpress backend. It's not a speed demon, but I think it's hard with such configuration to achive perfect performance - that's why I switched to Jekyll. In single post view are implemented Facebook comments, not the Wordpress ones.

# Details

I tried to write tests for Angular components and the `posts` service and pretty much made it. You can clone the repo and run the tests (configured to run with Karma in headless Google Chrome) using `npm test` command.

Angular - Wordpress communication lies in the `posts` service. It's tiny because I didn't need much. I planned to add custom post type for my portfolio entries (and call it projects maybe), but I decided it isn't necessary in a sample project.

I have created pretty big amount of components as for such small website because I wanted to have small pieces of code to maintain as Angular is new for me. 

On Wordpress backend I just had to install some CORS plugin to allow fetching data from API from other origins.

# The end

Thanks for reading! Use source from Github just like you want to. I didn't provide any code walkthrough as it's pretty straightforward - feel free to contact me if you have questions or open an issue on Github.
