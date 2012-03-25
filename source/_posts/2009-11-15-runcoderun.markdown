---
date: '2009-11-15 11:57:08'
layout: post
slug: runcoderun
status: publish
title: RunCodeRun
wordpress_id: '244922374'
categories:
- regular
---

For a personal project, I'm trying out [RunCodeRun](http://runcoderun.com), a service for doing automated builds for projects on [github](http://github.com).





I think the idea is a good one. For gems or simple web apps without complicated integration tests, getting an automated build up and running is dead simple. It's just a matter of adding a post-commit hook to your github project to notify runcoderun that the code has been updated.





I've run into a few issues with missing gems on the build machine, but they've been incredibly responsive. After posting a support request to install a gem, they not installed the gem I requested; they also installed a gem I didn't know was missing, forked my project to fix a gem dependency problem and a database configuration problem, and sent me a pull request. This is all within 24 hours, and for a service I'm not even paying for!





The service is free for Open Source code, but they have a paid build option for private projects with dedicated build resources. I haven't used the paid service, so I'm not sure to what extent they support more complex requirements like multiple database connections, system services (Sphinx), and distributed systems.





Hopefully, if [Relevance](http://thinkrelevance.com) is dedicating the resources to provide such great support, they'll also be improving the flexibility of the service for more complex builds. I doubt it would work in its current state for my current professional work, but I'd love to be able to easily outsource my builds.
