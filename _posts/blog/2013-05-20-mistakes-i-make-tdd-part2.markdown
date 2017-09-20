---
layout: post
title:  "Mistakes I make using TDD - part 2"
date:   2013-05-20 15:04:00 +0300
tags:  tdd c mocks unit-testing guard-cunit cunit system-testing integration-testing mistakes-i-make isolation
featured: true
categories: articles
---

Couple of months after I started this...

 Now I have some time to share more thoughts on what mistakes I made, when using TDD. 

Isolation

![My team]({{ site.url }}/assets/team.jpg)


Working in isolation is bad when you are writing software, and for TDD is especially bad and strongly against its principles, as far as I understand them.

I was in a situation that due to mostly political issues within the team I was quite reluctant to communicate the use cases with my peers. So I relied a lot on assumptions and documentation. Even modules that needed to be integrated were relatively well documented in advance via high level design documents, this definitely cannot replace direct, meaning real-time, communication, no matter informal face to face talk or chat via the network.

So in result of the above when I finished , "I thought", my 2 cents, I was feeling happy created quite stable module. I presumably covered all the top priority functionality, as we initially agreed/documented. On occasional checks from peers - "How is it going ?" 

, sometimes maybe sounded like Dilbert comics:

"Where is my status report"

, I tried to reply as fast as prompt as possible - "working", "all ok"... etc.

 So in result when I was done, it turned out I missed one functionality which initially was planned for later but then become important.

I was working with assumption - not important, peer was living with the idea - "all ok", meaning everything will be ready...

Also on some peculiar places there was obvious misunderstanding of the interface I should provide.

Bottom line, another week of work - not so bad - but we must target perfection, and also loosing a week simply because don't want to talk with a colleague - sounds stupid :(

 I fully understand the fault is mine, since I am doing the unit tests to cover certain use-case scenarios, I should make sure use-case scenarios are correct and handled with correct priority.

Unit tests are the first step ...
Every step you take...

Tests'll be watching you..

When working on a project that the module under change/test has a lot of interfaces between the new logic, and the user effect. In other words there are a lot of modules till user sees the effect of your change.

In this cases one should have consider testing on each step of integration, so  integration tests, system test, acceptance tests, should be carefully planned right after the unit tests, because higher level tests help to handle:

inter-module behaviour that was not well analyzed/predicted or even not known 
some of the use cases that arise only after high level testing that were not predicted by the unit test scenarios
often it reveals wrong old design decisions in other modules or the infrastructure
 
![It works]({{ site.url }}/assets/works_on_my_pc.png)


 I did system-level tests on a platform close to the real, but my colleagues couldn't test their code on it.  They needed to bring it up on different platform which again was not the target, close to it but not like mine.

 Anyways - I knew this from the very beginning , and just because wanted to deliver on time missed some points, which cost me another 5 days helping the guys to set up their system to simulate correctly the target. They simply had problems, which did not appeared in my case, so I ignored.

All of the above should be raised as soon as possible because usually hide big issues, which usually take a lot of time fixing.

After that it took us like a month to get working the real platform, and start the real platform, we could do it on either of the simulated environments, but every week we were expecting updated drivers for our target, and also it was "comfortable" time for the management to sneak some side tasks. As result first 2 days on real target resulted in 3 to 5 critical bugs that we could catch much earlier.

We should have pushed the management and ourselves also to reach as far as possible in testing the feature.

 A bit Off topic

During the whole effort I used a lot my tool guard-cunit . I started experimenting with it to add coverage reports via gcov reports to the running tests.

Seeing coverage on all the tests run looked nice, and in some case  you can see how you are deviating from the ideal target 100%. Not sure if I should invest in that feature though or better try to cover in the gem more C unit test frameworks. One of the reason for this doubt is that setting up manually usage of the gcov tool, maybe better solution will be to use it as C library in the gem, so I can optimize usage of the library.

In general I have a plan to invest some to get to know better the CppTest and Unity.

Anyways time will show