---
date: '2011-02-15 22:02:52'
layout: post
slug: mysql-mass-destruction-with-xargs
status: publish
title: MySQL Mass Destruction with xargs
wordpress_id: '3320438220'
categories:
- regular
---

Yesterday, I needed to clobber a bunch of similarly-named database schemas on my development machine. I could have selected and deleted 40 times in Navicat, but I thought I'd try to write a one-liner instead:





`  

mysql -u root -e "show databases;" | grep _3_6 | xargs -IDB_NAME mysql -u root -e "drop database DB_NAME;"  
`





The first part pulls the database names all the database names. The second part culls any schema names that don't match "_3_6", and the last part executes a DROP DATABASE command for each matching schema name.





The clever bit is the "-I" flag to xargs, which sets a token to be replaced with the argument in the command string. In this case, the schema name ("pp_development_3_6") is dropped in wherever xargs sees the string "DB_NAME" in the command.





_[Wikipedia attributes the xargs utility to PWB/UNIX](http://en.wikipedia.org/wiki/PWB/UNIX). It may have been written by [Dick Haight](http://www.ugu.com/sui/ugu/showclassic?I=info.Dick_Haight), who is, apparently, the 10 of Clubs in the [Unix 25th Anniversary Playing Card deck](http://www.ugu.com/sui/ugu/showclassic?I=info.usenix-cards), which, apparently, exists.  
_
