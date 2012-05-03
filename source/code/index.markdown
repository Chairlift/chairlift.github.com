---
layout: page
title: "Code Archives"
date: 2012-05-02 13:25
comments: true
sharing: true
footer: true
---
##How to configure [Nginx](http://wiki.nginx.org/Main) for [PHP](http://php.net/) and [Ruby on Rails](http://rubyonrails.org/)


Setting up Nginx can be tough.  Here's a basic configuration file found in the /etc/nginx directory.
{% gist 2582765 %}

By combining PHP-FPM and Nginx we get a robust php processor for rapid page loading across complex and multifaceted PHP web applications. It's worth mentioning that the following configuration leverages the unix socket for php-fpm processing, preferred over TCP sockets.
{% gist 2582278 %}

When we host many PHP sites, we use this type of conf file in the sites-available directory, symbolically linked to from sites-enabled as follows:
{% gist 2582593 %}
We set two server blocks. The first handles http browser requests on port 80. For secure request processing over https on port 443, the second server block is using SSL certs.

Next we'll talk about how to position the same PHP handling Nginx server to handle Ruby on Rails web applications with upstream blocks processed by <a href="http://unicorn.bogomips.org/">Unicorn</a> or <a href="http://code.macournoyer.com/thin/">Thin</a>.