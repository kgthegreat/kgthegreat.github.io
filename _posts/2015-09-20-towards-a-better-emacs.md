---
layout: post
title: Towards a better Emacs
---

This post lists some customizations and libs towards a better Emacs IMO. This is an evolving document.

-----

### Adding Marmalade

{% highlight lisp %}
;; In ~/.emacs/init.el
(require 'package)
(add-to-list 'package-archives
             '("marmalade" . "http://marmalade-repo.org/packages/") t)
(package-initialize)
{% endhighlight %}

### Better Defaults

{% highlight lisp %}
M-x package-install[RET] better-defaults
{% endhighlight %}

<a href="https://github.com/technomancy/better-defaults">Github Link</a>

### Smex
{% highlight lisp %}
M-x package-install[RET] smex

;; In ~/.emacs/init.el
;; smex
(global-set-key (kbd "M-x") 'smex)
(global-set-key (kbd "M-X") 'smex-major-mode-commands)
;; This is your old M-x.
(global-set-key (kbd "C-c C-c M-x") 'execute-extended-command)

{% endhighlight %}

<a href="https://github.com/nonsequitur/smex">Github Link</a>

### Window Navigation

{% highlight lisp %}
(global-set-key (kbd "C-x <up>") 'windmove-up)
(global-set-key (kbd "C-x <down>") 'windmove-down)
(global-set-key (kbd "C-x <right>") 'windmove-right)
(global-set-key (kbd "C-x <left>") 'windmove-left)
{% endhighlight %}

