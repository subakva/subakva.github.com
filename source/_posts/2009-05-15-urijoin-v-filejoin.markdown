---
date: '2009-05-15 19:12:00'
layout: post
slug: urijoin-v-filejoin
status: publish
title: URI.join v. File.join
wordpress_id: '108364423'
categories:
- regular
tag:
- ruby
- code
---

`URI.join` does not work quite the same way as `File.join` in Ruby. The aim of `URI.join` is more to calculate a relative path (as a browser would) than to simply concatenate path elements cleanly. The irb output below demonstrates this:




`

    
    irb> require 'uri' #=> true
    irb> host = 'http://www.example.com' #=> "http://www.example.com"
    irb> prefix = 'prefix' #=> "prefix"
    irb> file = 'file.html' #=> "file.html"
    irb> URI.join(host, prefix, file).to_s #=> "http://www.example.com/file.html"
    irb> URI.join(host, prefix+ '/', file).to_s #=> "http://www.example.com/prefix/file.html"
    


`
