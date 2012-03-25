---
date: '2010-04-22 14:39:11'
layout: post
slug: bulk-update-github-hooks
status: publish
title: Bulk Update Github Hooks
wordpress_id: '541130624'
categories:
- regular
---

The Github API doesn't support updating hooks, but I've got way too many projects going to do it by hand. I wrote up this script to update all of my hooks at once. I used the [mechanize](http://mechanize.rubyforge.org/mechanize/) gem to drive the web admin interface for the hooks that I needed.





The gist with the code is here: [[http://gist.github.com/375621](http://gist.github.com/375621)](http://gist.github.com/375621)
