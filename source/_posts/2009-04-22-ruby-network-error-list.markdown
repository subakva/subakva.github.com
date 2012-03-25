---
date: '2009-04-22 15:33:18'
layout: post
slug: ruby-network-error-list
status: publish
title: Ruby Network Error List
wordpress_id: '99000513'
categories:
- regular
---

I'm writing some code that needs to handle a failed network connection. Here's an almost certainly incomplete list of the exceptions I need rescue:




` SocketError,   Timeout::Error,   ActiveResource::TimeoutError,   Errno::ECONNREFUSED,   Errno::EHOSTDOWN,   Errno::EHOSTUNREACH `




How about an IOError or something?
