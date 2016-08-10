---
layout: post
title: Deploying a Golang app on Linux Server
---

This post lists the steps to get a golang app running on a linux server

-----

### Background

I am writing a recommendation engine in Golang and wanted to put up the initial version on the web. Hence this post. Please note that this may not be the recommended way. Quick and Dirty is the key phrase here.

### Steps

1. Get a VPS. I got one from Digital Ocean. Use this referral <a href="https://m.do.co/c/0e9b19aad9a9">link</a> to get some free credits for you and me.
2. Secure the VPS(Relatively speaking). Since my server was running Ubuntu, I followed this <a href="https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04">tutorial</a>
3. Cross compile your golang for the target OS and Architecture. More info <a href="http://dave.cheney.net/2015/08/22/cross-compilation-with-go-1-5">here.</a>

         {% highlight bash %}
         # More info <a href="https://golang.org/doc/install/source#environment">here</a> regarding OS and ARCH
         $ env GOOS=linux GOARCH=amd64 go build -v github.com/<github_id>/<project_path>
         {% endhighlight %}

4. SCP the executable

         {% highlight bash %}
         $ scp <executable> <username>@<ip>:/home/<username>/<app_dir>
         {% endhighlight %}

5. SCP any other assets required. In my case, I keep all assets inside a folder called static and html in a folder called templates so

         {% highlight bash %}
         $ rsync -av templates <username>@<ip>:/home/<username>/<app_dir>
         $ rsync -av static <username>@<ip>:/home/<username>/<app_dir>
         {% endhighlight %}

6. Since I am using RethinkDB,

         {% highlight bash %}
         $ source /etc/lsb-release && echo "deb http://download.rethinkdb.com/apt $DISTRIB_CODENAME main" | sudo tee /etc/apt/sources.list.d/rethinkdb.list
         $ wget -qO- https://download.rethinkdb.com/apt/pubkey.gpg | sudo apt-key add -
         $ sudo apt-get update
         $ sudo apt-get install rethinkdb
         {% endhighlight %}

         More info <a href="https://www.rethinkdb.com/docs/install/ubuntu/">here</a>

7. Run the binary. Access it at http://<ip>:<port>. 


