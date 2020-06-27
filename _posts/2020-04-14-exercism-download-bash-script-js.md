---
layout: post
title:  "Writing a Bash function to automate Exercism.io JS exercise setup"
featured: true
tags: [ bash, how-to, javascript ]
featured_image_thumbnail: /assets/images/posts/2020/04/14/cover.png
featured_image: /assets/images/posts/2020/04/14/cover.png
img_base_url: /assets/images/posts/2020/04/14
---

Lately I've been working my way through the JavaScript track on [Exercism.io](https://exercism.io/). It's an excellent website and I highly recommend checking it out if you either want to work on your skills in a particular language (there are 50 to choose from), or are comfortable in a particular programming language and interested in mentoring others.

[![Exercism.io]({{page.img_base_url}}/exercism-site.png)](https://exercism.io/)

Something I found a little repetitive was the process of setting things up to work on an exercise. The process went something like this:

1. open the exercise in the browser
2. copy the download command (e.g. `exercism download --exercise=collatz-conjecture --track=javascript`) from the browser window, and paste it into terminal
3. cd into the correct folder (e.g. `cd Exercism/javascript/collatz-conjecture`)
4. run `npm install` so that the tests are ready to be run

Pretty straightforward, but also a predictable and repeatable pattern... perfect for a bash function! Here's the command I want to be able to run in order to make all of the above execute (where the name of the exercise is 'collatz-conjecture'):

`$ devil collatz-conjecture`

To make this possible, here's the bash function that I added to my `.zshrc` (I use zsh so added it to my `.zshrc`, but if you're using bash, add it to your `.bashrc`):

```
devil() {
    exercism download --exercise=$1 --track=javascript && cd ~/Exercism/javascript/$1 && npm install;
}
```

Let's break it down. On line 1 is the name I've given to the function (devil), followed by parentheses and an open curly brace (standard function syntax). I named my function 'devil' because it's easy to type, and something I associate easily with 'exercism' (making it easy to remember).

Line 2 is where the awesomeness happens. These are all the steps I was previously doing 'manually', run for me by executing only one command. The `&&` between each command means that each command must succeed in order for the next one to execute. This makes sense in this context, because each command relies on the previous commands's success. For example, we can't cd into the folder in step 2 if it wasn't created in step 1. But what about the `$1`? That's the bash way of saying "grab the first argument passed in when the function is run, and use it here". So in our example above, `$1` would hold the value `collatz-conjecture`.

Line 3 is the closing brace to end the function.

So now all I need to know is the name of the next exercise I want to attempt on [Exercism.io](https://exercism.io/), and I can simply run `devil exercise-name` to have my bash function do all the setup work for me!

Here's what it looks like in action:

{% asciicast 319489 %}

{% include_relative post-back-matter.md %}