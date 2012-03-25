---
date: '2011-11-09 21:41:00'
layout: post
slug: book-review-test-driven-infrastructure-with-chef-by-stephen-nelson-smith-oreilly-media
status: publish
title: 'Book Review: Test-Driven Infrastructure with Chef by Stephen Nelson-Smith;
  O''Reilly Media'
wordpress_id: '12583398300'
categories:
- regular
tag:
- tech
- book-review
- oreilly
- chef
- devops
---


![](http://media.tumblr.com/tumblr_lufbogviud1qzzhm0.gif)





#### Summary





[Test-Driven Infrastructure with Chef](http://shop.oreilly.com/product/0636920020042.do) describes a rationale and an approach to developing automated tests for system infrastructure. It includes an explanation of behavior-driven development, and detailed instructions for setting up a testing system using [cucumber-chef](https://github.com/Atalanta/cucumber-chef) on EC2.






#### Audience





Surprisingly little time was spent talking about cucumber-chef and how to use it. The majority of the book is spent explaining BDD and why you'd want to apply it to infrastructure, and then explaining in minute detail the process to get [RVM](https://rvm.beginrescueend.com/), [EC2](http://aws.amazon.com/ec2/) and [Chef](http://www.opscode.com/chef/) configured. The last portion of the book covered the process of using [cucumber-chef](https://github.com/Atalanta/cucumber-chef) to set up a server with multiple user accounts.







Being already familiar with the supporting tools, I found this disappointing. The teamserver example was too simple and unrealistic. It would have been more useful to see some examples using cucumber-chef for a more realistic use-case, such as setting up a web server.







Unfortunately, I suspect the text isn't likely to be helpful to a reader who _isn't_ familiar with the tools either. The instructions were already outdated when I read them, shortly after the book was released. A reader who is new to Cucumber, Chef, Ruby or EC2 will be in danger of getting lost before they even get to the point where they can run a test against an instance.






#### Practicality






In the course of working through the examples, I was continually frustrated by the amount of time it took to get feedback. The tests are really slow. It's hard to imagine actually developing red/green/refactor-style at this pace. I like the concept of being able to test the infrastructure, but it doesn't seem practical with these tools.







I'm not convinced that it would really be worth the time involved to write tests at this level anyway. Writing integration tests against the full application stack might be a better use of your testing time. The true test of the infrastructure is how well it supports needs of the application and it's users.







Neither BDD-style infrastructure tests nor full-stack integration tests will help you with the most difficult and interesting infrastructure challenges: scaling and stability. Simulating all the wonderful ways that a server can crash (used up disk space, hung connections, etc.) would be a complex, difficult, slow, and inevitably incomplete endeavor. It's possible that server ops really is fundamentally different than application development.






#### Bottom Line




  * Good explanation of BDD and how it could be applied to infrastructure


  * Short on useful examples for readers familiar with the supporting tools


  * Thorough instructions for setting up EC2, Chef and RVM, but likely to have a short shelf-life




Available from  O'Reilly: [Test-Driven Infrastructure with Chef](http://shop.oreilly.com/product/0636920020042.do)

