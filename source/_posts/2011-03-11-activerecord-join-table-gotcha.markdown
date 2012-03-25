---
date: '2011-03-11 20:10:30'
layout: post
slug: activerecord-join-table-gotcha
status: publish
title: ActiveRecord Join Table Gotcha
wordpress_id: '3795383974'
categories:
- regular
---

Whenever I create join tables, I'm always tempted to add an ID column, in case I want to upgrade it to a :through association at some point. I'm also tempted to timestamp columns, so that I can know when the association was created.





Sadly, it just doesn't work with `has_and_belongs_to_many`.





- If you add an ID column, Rails will choke as soon as you try to access it. IDs are not allowed!  

- If you add timestamps, Rails will make all of your association records readonly. 





If you want to have an ID and timestamps, you'll just have to bite the bullet and create an association model and a `has_many :through` relationship.





Maybe now that I've written about it, I'll remember it next time and save myself debugging mysterious `"ActiveRecord::ReadOnlyRecord: ActiveRecord::ReadOnlyRecord"` errors.
