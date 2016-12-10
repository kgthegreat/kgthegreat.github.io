---
layout: post
title: Run goimports on file save in emacs
---

This post documents how to run goimports with every file save in Emacs

-----

### Get goimports

goimports is a drop-in replacement for gofmt

{% highlight bash %}
$ go get golang.org/x/tools/cmd/goimports
{% endhighlight %}

### Change init.el

Change the emacs init file

{% highlight lisp %}
(setq gofmt-command "goimports")
(add-hook 'before-save-hook 'gofmt-before-save)
{% endhighlight %}

{% highlight bash %}
M-x eval-buffer
{% endhighlight %}

