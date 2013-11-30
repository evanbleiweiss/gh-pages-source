---
layout: post
title: "What are class methods for?"
date: 2013-11-30 11:20:52 -0600
comments: true
categories: 
---
I've been working on building a small toolset that abstracts many of the details of small, repetitive tasks that I frequently need to do.  In the REPL, I typically assign a few variables to class instances that I need to modify, then do whatever manipulation I need to do to the data underlying the instance I'm updating.  This works fine and I sometimes call methods directly on my instances, and sometimes I pass them into a class method that takes the variable's properties as an argument.  The thing I haven't figured out is the interface for that I want my toolset to use when it automates the steps in an process for me.

- I don't expect there to be multiple versions of the same task running at one time.  This is something where an instance makes a lot of sense to me.
- I don't necessarily need there to be **only one** initialized version of the class where these tools live.  I don't really care if there is 1 or 42 of these tasks in memory.  They aren't designed to rely on things like shared values in memory, and don't need to be a singleton.

So, all I really need is for my class to accept some number of arguments (typically, this is known, and does not rely on dynamic or generated values), then take those arguments and run them through a few scripts.

A colleague of mine suggested to me that there is no need for class methods, and their use represents a design flaw. _This might be paraphrasing somewhat, as he might allow some exceptions to this rule_.  However, the code for having an `initialize` method, vs wrapping my methods in `class << self` is a few lines of code, and, perhaps confusion over the expected usage of the tools.

So, what's the most correct thing to do?  These aren't going to be used outside of a periodic bout of sysadmin behavior, but is there something fundamentally _"wrong"_ about using a class method for this purpose.

Perhaps some code examples would clarify...
