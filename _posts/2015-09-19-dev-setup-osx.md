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

#### How to stop brew from upgrading certain formulas

When
{% highlight bash %}
$ brew upgrade
{% endhighlight %}
is issued, brew will update all the formulas.
To stop certain formulas from upgrading, do this
{% highlight bash %}
$ brew pin certainformula
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
$ export JAVA_HOME=`/usr/libexec/java_home`
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
# check
$ node -v
$ npm -v

# Upgrade node
$ brew update
$ brew upgrade node
{% endhighlight %}


### Redis

{% highlight bash %}
$ brew update
$ brew install redis
# To have launchd start redis at login:
$ ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
# Then to load redis now:
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
# Or, if you don't want/need launchctl, you can just run:
$ redis-server /usr/local/etc/redis.conf
{% endhighlight %}


### Mule ESB

You can use mule in conjunction with AnyPoint IDE(Eclipse based) or as standalone runtime, which I prefer.
Download the community edition standalone from https://developer.mulesoft.com/download-mule-esb-runtime
Extract the zip and probably place it to a dir where you normally put software. For me it is ~/installs

{% highlight bash %}
$ cd <where_you_unzipped_mule>
# To start mule 
$ ./bin/mule
# To start mule as daemeon
$ ./bin/mule start
# To stop|restart
$ ./bin/mule stop|restart
{% endhighlight %}

To deploy applications to the standalone mule runtime, drop your project's zip file to $MULE_HOME/apps and start mule

### Groovy

{% highlight bash %}
$ brew update
$ brew install groovy
# Set GROOVY_HOME
$ export GROOVY_HOME=/usr/local/opt/groovy/libexec
{% endhighlight %}

### Grails

{% highlight bash %}
$ brew update
$ brew install grails
# Set GRAILS_HOME
$ export GRAILS_HOME=/usr/local/opt/grails/libexec
{% endhighlight %}


### Tree

Tree is a command line utility to view content of a dir in a tree like structure

{% highlight bash %}
$ brew update
$ brew install tree
{% endhighlight %}


### Mongo DB

{% highlight bash %}
$ brew update
$ brew install mongodb
{% endhighlight %}

### Golang

{% highlight bash %}
# Recommended: $HOME/go. I use $HOME/code/go
$ export GOPATH=$HOME/code/go
$ export PATH=$PATH:$GOPATH/bin
$ brew update
$ brew install go
$ go version
{% endhighlight %}

<a href="https://golang.org/doc/code.html">Hat Tip</a>

### Gradle

{% highlight bash %}
$ brew install gradle
{% endhighlight %}

### Pip

{% highlight bash %}
$ sudo easy_install pip
{% endhighlight %}

### AWSCLI

{% highlight bash %}
$ pip install awscli
# If there is an error "Uninstalling a distutils installed project (six)..." on El Kapitan then use the following command
$ sudo pip install awscli --ignore-installed six
{% endhighlight %}

### RethinkDB

{% highlight bash %}
$ brew update && brew install rethinkdb
{% endhighlight %}

### ssh-copy-id

{% highlight bash %}
$ brew update && brew install ssh-copy-id
{% endhighlight %}

### python3

{% highlight bash %}
$ brew update && brew install python3
{% endhighlight %}

### [fswatch](https://github.com/emcrisostomo/fswatch)

{% highlight bash %}
$ brew update && brew install fswatch
{% endhighlight %}

