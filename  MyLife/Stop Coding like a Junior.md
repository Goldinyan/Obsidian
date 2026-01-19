Date: 2026-01-19
Tags: {
#W
}


# Stop Coding like a Junior

## 1 - The Deploy

After a hard week, you finish a feature and after succesfull attempts you deploy the code. You are happy and releaved. You feel like nothing could stop you.
The next day you get a call: "Hey, there are many weird support tickets, could you check that out?"
Your tests were green, and everything worked. But Users are crazy, they try and do actions, you would never knew someone could. 
Your code needs to be user-safe. 


## 2 - The Wrong Layer

print statements wont cut it, to really debug and not sit hours on a very easy bug. You need to undestand the problem, use the appropriate tools, like a debugger,  look at the logs, and really go thourgh anything step by step.

## 3 - The Scroll of Shame

You write an application which takes articles-data and provides a user interface for it. Everything works simple and you finish it in a quite memorable time.
4 days later, a manager contacts you: "Hey, so the page needs 54 seconds to load. Is it supposed to be this delayed?"
Ofcousre not. So you gather a meeting and sit with them, and then you open the logs. SQL Queries over SQL Queries. 
It was 200 articles, and 200 SQL Queries for the article, 200 for the author, and 200 for the tags.
You ddos your own SDL db.
All because you wanted to abstract layers and trust everything, but understanding the layer that being abstarcted is required or you will run into these issues.

## 4 - Expensive Mistakes

Simple tasks about improving Stripe web hooks for thousand of transactions daily, but payments *fail*. The code works for successful payments, failure was an edge case and not a main concern, but it should be a primary cconcern.
A customer credit card got declined. Normal thing, happens all the time but the code threw an unhandled exception, leading to the web hook returning a 500 error to Stripe. 
When a Stripe web hook fails, it retries.
Over 
and *over*
and **over**
again. 
Dozens of retries over 72 hours, every single one of them triggering a lambda that failed, but not before htting our database inventory system. Thus, the AWS bill raising noticeably.
*One failed payment cascaded into real infrastructure costs.*

>The happy path is the least important path. Every user will hit it and it's the most tested. It's all about the failure paths that matter, because those are the ones that break your systems.

Its not just the users dissatisfaction, but it's also real costs attached to the infrastructure.

## 5 - The week that never shipped

New ticked, new ideas. 
Asking felt like admitting I didn't know what I was doing.
So I did it myself. The manager was gone over the weekend, so, to impress him, I just kept building. 
About a week of work, thousands of lines of code, clean, tested, and documented. I was proud.
Demo day. Manager's first question: "Why didn't you just use Google Analytics? That would have taken an hour"
The didn't need new infrastrucute, they only needed a few lines of JavaScript. A week of work, never shipped, probably still sitting in an old branch somewhere.
After that, my manager gave me 3 questions to ask myself before every task:
- What problem am I solving?
- Is there an existing solution?
- What's is the simplest thing that works?
 This is the base of the [[30 Minute Rule]].
 
 >Over-engineering sucks. Plan before Implementation.
 





# References