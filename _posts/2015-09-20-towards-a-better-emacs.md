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
M-x package-install[RET] better-defaults [RET]
{% endhighlight %}

<a href="https://github.com/technomancy/better-defaults">Github Link</a>

### Smex
{% highlight lisp %}
M-x package-install[RET] smex [RET]

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

### Find files in git project

{% highlight lisp %}
M-x package-install [RET] find-file-in-repository [RET]
{% endhighlight %}

<a href="https://marmalade-repo.org/packages/find-file-in-repository">More info</a>

### Ignoring certain files and folders while doing grep

{% highlight lisp %}
;; Ignoring certain directories while doing rgrep
(eval-after-load "grep"
  '(progn
     (add-to-list 'grep-find-ignored-files "*.tmp")
     (add-to-list 'grep-find-ignored-directories "node_modules")
     (add-to-list 'grep-find-ignored-directories "dist")))
{% endhighlight %}

### Duplicate a line

{% highlight lisp %}
(defun duplicate-line()
  (interactive) 
  (move-beginning-of-line 1)
  (kill-line)
  (yank)
  (open-line 1)
  (next-line 1)
  (yank)
)
(global-set-key (kbd "C-d") 'duplicate-line)
{% endhighlight %}

<a href="http://stackoverflow.com/a/88828/178975">Hat Tip</a>

### Auto complete

{% highlight lisp %}
M-x package-install-packages
;; Search for auto-complete in MELPA, mark it to be installed by pressing i at the column and then press x to install
{% endhighlight %}

<a href="http://auto-complete.org/doc/manual.html">More info</a>

### Keep auto save files out of current dir

{% highlight lisp %}
(setq backup-directory-alist
          `((".*" . ,temporary-file-directory)))
(setq auto-save-file-name-transforms      
          `((".*" ,temporary-file-directory t)))
{% endhighlight %}


### Running emacs as daemon

I have added the following lines to my shell rc

{% highlight bash %}
alias ed="emacs --daemon"
alias ec="emacsclient -t"
alias ek="emacsclient -e '(kill-emacs)'"
{% endhighlight %}

### Zenburn Theme

{% highlight bash %}
M-x package-install zenburn-theme
(load-theme 'zenburn t)
{% endhighlight%}

### JS editing

{% highlight lisp %}
M-x package-install[RET] js2-mode [RET]
M-x package-install[RET] ac-js2 [RET]

(add-hook 'js-mode-hook 'js2-minor-mode)
(add-hook 'js2-mode-hook 'ac-js2-mode)
(setq js2-highlight-level 3)
{% endhighlight %}


### Keys

Follow [this](http://azaleasays.com/2013/07/05/setting-up-mac-os-x-and-iterm2-for-emacs/)

### Speedbar in the current frame

Speedbar is great for tree navigation. It comes with emacs 24+ by default. To open speedbar in current frame, use [this](https://www.emacswiki.org/emacs/SrSpeedbar)

### Find any file in a git project

Use [helm](https://emacs-helm.github.io/helm/) and [helm-ls-git]() to get a fast and fantastic project browser.

{% highlight lisp %}
M-x (global-set-key (kbd "C-x C-d") 'helm-browse-project)
{% endhighlight %}