---
title: Test Debugging Development - The bad kind of TDD
layout: article
---

> “Look, we have become masters of rspec, jest and unittest.” 

It’s Monday and I go over to the board and get a feature to work on. 

I pick a feature that seems in line with my skill level. I already know what I am going to do. I become excited because I find one that is straightforward.

I add the API endpoints and test them out on Postman. On the browser, the UI is responsive and everything is working as expected. 

The work is finished and it’s time to open a pull request. Hold up, there’s one last thing that you have to do. Write the tests.

I know that even if I open a PR, it won’t cut it because the team expects tests to be written for every feature. 

I start going over every file that I touched and seeing if there’s a corresponding test file and adding the tests there. But it takes more time than usual to finish up the tests.

When standup comes around, I tell the team that I have a blocker. If only they knew that the blocker is actually not related to the feature but I’m having an issue getting a serialiser test to initialise correctly. 

In the end, I find that I am jumping into rabbit holes trying to learn something about the test framework and not the language itself. It’s a dangerous cycle to fall into. 

I have fallen into the trap several times. The problem is that this cycle starts to make software development agonising to do and takes the fun away from it. I find that I spend more time figuring out why the tests don’t pass instead of the actual development work itself. 

There’s something about writing tests first that gives me the confidence in the code. Not surprisingly, it also leads to fewer errors.

