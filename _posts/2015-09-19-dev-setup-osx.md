---
layout: post
title: Development Environment on OSX
---

In this post I document the steps required to install various tools and environment to start development on OSX 10.10 (Yosemite). This is an evolving document.

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

### Java

Download from Oracle's website

{% highlight bash %}
# To set JAVA_HOME
$ export JAVA_HOME=/Library/Internet Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/
{% endhighlight %}


### Autojump

{% highlight bash %}
# Pretty nifty directory navigation tool
$ brew install autojump
# Add the following to your .bash_profile(or equivalent)
[[ -s $(brew --prefix)/etc/profile.d/autojump.sh ]] && . $(brew --prefix)/etc/profile.d/autojump.sh
{% endhighlight %}


### ZSH

{% highlight bash %}
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
{% endhighlight %}

### Browser Plugins

1. Adblock
2. Privacy Badger
3. HTTPS Everywhere

### Mysql

{% highlight bash %}
# Install using brew
$ brew install mysql
# To run the server
$ mysql.server start
# To connect:
$ mysql -uroot
# To have launchd start mysql at login:
$ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
# Then to load mysql now:
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
{% endhighlight %}

### Maven

{% highlight bash %}
$ brew install maven
$ mvn -version
{% endhighlight %}

### Composer

{% highlight bash %}
# Install composer in your pwd. Requires PHP. 
$ curl -sS https://getcomposer.org/installer | php
# To use
$ php composer.phar
# Move it to a directory under PATH if you need it globally
$ mv composer.phar /usr/local/bin/composer
# Use it
$ composer
{% endhighlight %}

### mcrypt

{% highlight bash %}
$ brew tap homebrew/php
$ brew install php55-mcrypt
{% endhighlight %}

### Memcache

{% highlight bash %}
$ brew install libmemcached
$ brew install php55-memcached
# Run the server
$ memcached -d
{% endhighlight %}


### Node and NPM

{% highlight bash %}
$ brew install node
$ node -v
$ npm -v
{% endhighlight %}
