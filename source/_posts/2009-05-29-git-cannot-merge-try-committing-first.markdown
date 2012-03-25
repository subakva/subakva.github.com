---
date: '2009-05-29 18:05:03'
layout: post
slug: git-cannot-merge-try-committing-first
status: publish
title: Git Cannot Merge? Try committing first.
wordpress_id: '115019773'
categories:
- regular
---

I ran into this git error again today:


    
    <code>
    Entry 'blah/blah.rb' would be overwritten by merge. Cannot merge.
    </code>



After messing around with it for a while, I remembered the last time this happened. The solution is to commit your current conflicting changes, then merge afterwards.
