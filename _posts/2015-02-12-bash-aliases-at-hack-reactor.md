---
layout: post
title: Bash Aliases at Hack Reactor
---

At Hack Reactor, students have to perform many routine tasks everyday. I set up a couple [Bash aliases](http://tldp.org/LDP/abs/html/aliases.html) to save time by running several tasks automatically. Hack Reactor calls these time-saving inventions “force multipliers” because it multiplies your effectiveness since you don’t have to spend your time doing the same things over and over. Here are a few of my most useful time savers:

## Toy Problems

Every morning students work on “Toy Problems” which are interview-style programming problems similar to CodeWars katas. The whole process uses a git workflow. There is a main, upstream branch which every student forks as their local repos. After that initial set up, the daily ritual of pulling new problems goes like this:

  1. Enter the directory: `cd toy-problems`
  2. Pull from the upstream repo: `git pull upstream master`
  3. Merge new file in (Control-X + Enter in nano editor)
  4. Open up Sublime: `subl .`

Every single step is performed in the command line in the exact same way everyday, which is perfect for automating with an alias.

We can write an alias using multiple lines of commands by writing a Bash function. Bash functions are structured similar to JavaScript functions defined by adding open and close parens after the function name and enclosing the function definition with curly braces.

Bash aliases and functions should be added to your .bashrc (or .zshrc if you use zsh) which get loaded for every new session in your terminal. 

My toy problem alias looks like this:

{% highlight bash %}
toy() {
  cd ~/toy-problems
  git pull —no-edit upstream master
  subl .
}
{% endhighlight %}

By running `toy` in the command line, it cd’s into the right folder. Then it does a git pull. The “-no-edit” flag automatically merges the new file and does not ask me to look at it. Then it opens sublime into the Toy Problem folder for me to begin working. Awesome.

But wait, there’s more!

When finished with the problem, I made another alias to submit it. The manual way is to open up git, look for the Hack Reactor repo, open the Pull Request page, look for your repo, look for your branch, and then finally click the Open Pull Request button.

I aliased this into 

{% highlight bash %}
alias toypr=“open https://github.com/bcbcb/2014-12-toy-problems/compare/hackreactor:bcbcb...bcbcb:master”
{% endhighlight %}


Now when I type `toypr` in the command line, it opens up Github with  Github thankfully makes this easy by having a consistent URL for comparing to branches from different repos. Modify the URL appropriately for your own account and repo. 

I recommend not blindly copy-and-pasting aliases if you don’t know what every step does. Not only is it a good learning experience to figure out new commands, but you also might run something you didn’t want to run.
 
