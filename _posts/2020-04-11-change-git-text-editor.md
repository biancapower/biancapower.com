---
layout: post
title: "How to change your default text editor for git (and avoid vim)"
featured:
tags: [ git, tips, how-to ]
featured_image_thumbnail: /assets/images/posts/2020/04/11/cover.png
featured_image: /assets/images/posts/2020/04/11/cover.png
img_base_url: /assets/images/posts/2020/04/11
---

We've all done it. `git add .` then... `git commit`. Big mistake. We forgot to add a `-m` with a message! Now we're in the dreaded vim text editor...

{% asciicast 318599 %}

_But what if there was another way?_ By changing the git config, we can specify **a different editor for git to launch us into** if it needs to do so. Below is how to do this on a unix (OSX or Linux) system.

First, **check what your current system default is** (you can pause the video below and copy the text command out of it - try it now!):

{% asciicast 318597 %}

In the example above, as on many systems, the default editor is vim. Personally, I love vim, but if you're not familiar with it it can make things a bit difficult and really mess up your flow. First let's look at **how to change git's default text editor to nano**, and what nano looks like in practice:

{% asciicast 318600 %}

As you can see, nano is much more straight forward than vim (not least because it gives you the commands you need at the bottom of the screen!), but it still exists completely in the terminal (which has pros and cons).

What if you want to change the editor used by git to something external to the terminal, like **VS Code**? Here's how:

{% youtube "https://www.youtube.com/watch?v=R9u2e66IKzc" %}

Note that changing the editor to `code` didn't work quite as we wanted it to - because we're leaving the terminal environment in order to go and edit the file in VS Code, we need to tell git to wait for us. We do that by specifying `code --wait`, which basically says "Hey git, I'm gonna go over to VS Code to edit that file now, just hang about, and once I've closed that file you can read it and finish processing the command".

The process for changing the default to other text editor is basically the same, it's just a matter of finding the correct key word(s) for launching the editor.

What do you use as your default text editor? Comment below!

{% include_relative post-back-matter.md %}