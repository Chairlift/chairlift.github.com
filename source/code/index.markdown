---
layout: page
title: "Code Archives"
date: 2012-05-02 13:25
comments: true
sharing: true
footer: true
---
##How to configure Nginx for PHP and Ruby on Rails


Setting up Nginx can be difficult.  Here's a basic configuration file found in the /etc/nginx directory.
{% gist 2582765 %}

By combining PHP-FPM and Nginx we get a robust php processor for rapid page loading across complex and multifaceted PHP web applications. It's worth mentioning that the following configuration leverages the unix socket for php-fpm processing, preferred over TCP sockets.
{% gist 2582278 %}

When we host many PHP sites, we use this type of conf file in the sites-available directory, symbolically linked to from sites-enabled as follows:
{% gist 2582593 %}
We set two server blocks up there in that conf file. The former handles http requests on port 80. For secure request processing over https on port 443, the second server block is using SSL certs.

We'll be updating next on how to position the same nginx server that is handling PHP to also handle Ruby on Rails web applications with upstream blocks processed by Unicorn.