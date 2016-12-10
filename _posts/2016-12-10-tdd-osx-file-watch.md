---
layout: post
title: Running tests on file change
---

Run tests (or any other command) on file changes

-----

I use [fswatch](https://github.com/emcrisostomo/fswatch) to watch files and run commands when the file changes.

### Installation

{% highlight bash %}
$ brew update && brew install fswatch
{% endhighlight %}

### Usage

I use it to run a single command while watching the current directory

{% highlight bash %}
$ fswatch -o . | xargs -n1 -I{} go test -v
{% endhighlight %}

So, in general
{% highlight bash %}
$ fswatch -o /path/to/watched/files | xargs -n1 -I{} <command>
{% endhighlight %}


