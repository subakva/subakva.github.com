---
date: '2009-11-25 1:13:27'
layout: post
slug: remove-an-environment-variable-in-bash
status: publish
title: Remove an Environment Variable in Bash
wordpress_id: '256607412'
categories:
- regular
tag:
- bash
- programming
---

`export -n RAILS_ENV`





Setting an environment variable to nothing is not the same as removing it entirely. If really need it to go away completely, use the `-n` flag on `export`.





**Behold:**




    
    <code>
    jason@idaho:~/Code/subakva$ env | grep RAILS_ENV
    jason@idaho:~/Code/subakva$ export RAILS_ENV=development
    jason@idaho:~/Code/subakva$ env | grep RAILS_ENV
    RAILS_ENV=development
    jason@idaho:~/Code/subakva$ export RAILS_ENV=
    jason@idaho:~/Code/subakva$ env | grep RAILS_ENV
    RAILS_ENV=
    jason@idaho:~/Code/subakva$ export -n RAILS_ENV
    jason@idaho:~/Code/subakva$ env | grep RAILS_ENV
    jason@idaho:~/Code/subakva$
    </code>
