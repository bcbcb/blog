---
layout: post
title: 2 Essential Sublime Plugins For Web Development
---

Sublime is a great editor, and there are lots of useful plugins. Some of them are handy to have, and then there are some that you can’t live without. 

Here are, in my experience, the 2 most helpful Sublime plugins for web developers. I would have picked 3 but I couldn’t think of any that were as essential as these two.

## SublimeLinter

A linter validates your code’s syntax and let’s you know where you screwed up. Having a linter in Sublime that shows you where there are errors is extremely valuable and saves you so much time and headaches.

For example if you write:

{% highlight js %}
console.log('missingendquote!);
{% endhighlight %}

The linter would highlight not only this line, but also the specific characters that are causing syntax errors. If you don’t have a linter, you would have to scan the file with your own eyes while parsing syntax in your head. Stop doing that and save your brainpower for more important things.

The most popular linter plugin is SublimeLinter. SublimeLinter itself isn’t language specific, so that means you’d have to install extra things to get it to lint whatever language.

For JavaScript linting in Sublime, you can do the following: 

  * Install SublimeLinter in Sublime Package Manager
  * Install SublimeLinter-jshint in Sublime Package Manager
  * If you don’t have node, install node
  * Install jshint through npm as a global module: `npm install -g jshint`


## GitGutter

If you use git for version control, whether in a team or by yourself, you probably know how valuable it is to see differences between commits. You can see this with the `git diff` command or on Github.

Git diffs show you which lines have been changed, added, and deleted by highlighting the lines in red or green and also by adding icons like plus or minus before those lines. 

With the GitGutter plugin, as you edit a file, similar icons on those same lines show up as if it were diff-ing in real time. This is useful for knowing how your commits will affect your repo.

This plugin saves lots of time when you forget exactly what you changed, or if those changes were worth adding.

## Other plugins?

Yes, there are lots of other cool plugins. 

But if you do web development, and you use Sublime and Git, install these 2 first.
