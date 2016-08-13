---
layout: post
title: Deploying a Golang app on Linux Server
---

This post lists the steps to get a golang app running on a linux server

-----

### Background

I am writing a recommendation engine in Golang and wanted to put up the initial version on the web. Hence this post. Please note that this may not be the recommended way. Quick and Dirty is the key phrase here.

### Steps

* Get a VPS. I got one from Digital Ocean. Use this referral <a href="https://m.do.co/c/0e9b19aad9a9">link</a> to get some free credits for you and me.
* Secure the VPS(relatively speaking). Since my server was running Ubuntu, I followed this <a href="https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04">tutorial</a>
* Cross compile your golang for the target OS and Architecture. More info <a href="http://dave.cheney.net/2015/08/22/cross-compilation-with-go-1-5">here</a>. More info <a href="https://golang.org/doc/install/source#environment">here</a> regarding OS and ARCH.

{% highlight bash %}
$ env GOOS=linux GOARCH=amd64 go build -v github.com/<github_id>/<project_path>
{% endhighlight %}

* SCP the executable
{% highlight bash %}
$ scp <executable> <username>@<ip>:/home/<username>/<app_dir>
{% endhighlight %}
* SCP any other assets required. In my case, I keep all assets inside a folder called static and htmls in a folder called templates so
{% highlight bash %}
$ rsync -av templates <username>@<ip>:/home/<username>/<app_dir>
$ rsync -av static <username>@<ip>:/home/<username>/<app_dir>
{% endhighlight %}

* Since I am using RethinkDB, it needs to be installed. More info <a name="rethinkdb" href="https://www.rethinkdb.com/docs/install/ubuntu/">here</a>
{% highlight bash %}
$ source /etc/lsb-release && echo "deb http://download.rethinkdb.com/apt $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/rethinkdb.list
$ wget -qO- https://download.rethinkdb.com/apt/pubkey.gpg | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install rethinkdb
{% endhighlight %}

* You may want to run RethinkDB as a service
{% highlight bash %}
$ sudo cp /etc/rethinkdb/default.conf.sample /etc/rethinkdb/instances.d/instance1.conf
$ sudo vim /etc/rethinkdb/instances.d/instance1.conf
$ sudo /etc/init.d/rethinkdb restart
{% endhighlight %}

* Run the binary. You may want to run it with nohup so that the process stays alive even after your session. Remember, quick and dirty. There are other better ways to do this.
{% highlight bash %}
$ nohup ./<binary_name> &
{% endhighlight %}

* Access it at http://[ip]:[port] 

* Stop the process
{% highlight bash %}
# This will give you the pid
$ ps -aux | grep <binary_name>
# use the pid obtained above
$ kill -9 <pid>
{% endhighlight %}


