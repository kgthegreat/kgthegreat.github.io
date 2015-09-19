---
layout: post
title: Development Environment on OSX
---

In this post I document the steps required to install various tools and environment to start development on OSX 10.10 (Yosemite). This post will always be WIP.

-----

### Homebrew

{% highlight bash %}
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

### Emacs

{% highlight bash %}
$ brew update
$ brew install emacs --with-cocoa

# Symlink to Applications
$ ln -s /usr/local/Cellar/emacs/24.x/Emacs.app /Applications
{% endhighlight %}

### Git

{% highlight bash %}
$ brew update
$ brew install git 
{% endhighlight %}

### Generate SSH Keys

{% highlight bash %}
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Ensure ssh-agent is enabled
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa


# Copy
$ pbcopy < ~/.ssh/id_rsa.pub
# Paste in your github account if required
{% endhighlight %}

### RVM and Ruby

{% highlight bash %}
$ \curl -sSL https://get.rvm.io | bash
{% endhighlight %}

Optional
{% highlight bash %}
# Install ruby 2.2
$ rvm install 2.2

# Install bundle as a global gem
$ rvm @global do gem install bundler
{% endhighlight %}