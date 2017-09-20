---
layout: post
title:  "Mistakes I make using TDD - part 1"
date:   2013-01-18 12:22:00 +0300
tags:  tdd c mocks unit-testing  mistakes-i-make
categories: tags
featured: true
---

In this and hopefully not long but useful series of posts I will try to track down mistakes I made using TDD. I am doing it with the hope that recording them will allow me not to repeat them a lot ;) and to gains some knowledge of it.

Most of the cases I will mention will be for using TDD in C, since that is my day-to-day job. I will be happy of course on comments from other people - even if they are - how could u be so stupid mate :)

 I will start with two examples that I ran into recently.

 * Memory Leak

Recently got into a memory leak issue, although my code's functionality seem to me quite thoroughly tested. The functionality was massively interfacing with external library and I made mocks and stubs for the APIs of that library. In the parallel did a lot of exploratory testing to make sure the MOCKs and flow are OK.

BUT

I didn't know the library very well. Simply not prepared good enough my homework and became the caricature of XP - doing lots of coding without preparing well enough with the provided documentation.

SO

I used API which were allocating memory, without knowing I should use also another API, which frees allocated resources, and thanks that within the team we did during the Christamss/NY  holidays tests that were supposed to check for such kind of problems so it got noticed.

 * Functionality was spoiling input parameters.

 I was doing patches for endianess on a driver. The case was that the certain data should have been converted from Big Endian to Little Endian notation. Again I think I covered lots of use-cases.

BUT

My tests were doing checks of type :

PrepareInputData

CallTheFuncUnderTest(Input,&Output)

CheckOutputAgains(Output,SomePredefinedExpectation)

SO

A bug appeared that every even call of my code was spoiling the input data. Strange right... For good or bad this C programming, my friend, and pointers are just pointers. I should have been much more careful not to touch input data.

 A possible solution would be besides testing output also testing input data. Of course in some cases I could simply protect that input data with using language mechanisms, although to be honest that will never be my first choice.  
