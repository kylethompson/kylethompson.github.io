---
layout: post
title:  "Live Operations Turns Junior Developers into Seniors"
description: "Supporting code in production is one of the best learning experiences a developer can get."
date:   2019-12-10 12:00:00
---

I'm often asked what the difference between a junior and a senior engineer is, or how can I become a senior quicker. There's not really an industry wide standard and so expectations can be wildly different between locations, projects and companies. From my experience, there are a few things that people often mistake for being tickets to the mythical world of 'senior'

#### Years Experience

Nope. While this can be a useful guide, 15 years experience of doing the same 12 months 15 times isn't really good for anyone. Anecdotally from my own experience, the average developer working in the right environment takes a few years to reach a senior level. Of course, it can be done quicker and also much slower depending on the individual's appetite, however a few years has always seemed like a decent guide.

#### Created a design document

It's on the right track, but it's certainly not a case of ticking the box once and become a senior engineer. Being able to reason about design decisions and tradeoffs is an important part of a senior engineer's day and therefore a critical activity that juniors need exposure to and coaching on. Understanding the constraints on your code is the first step to creating an effective design and so junior developers should be given a chance to demonstrate they can factor in, for example, what is the user need? are we satisfying it with this design or have we missed the point? how will this be built and deployed? how will it be tested / have we cleanly seperated dependancies?  do we have to compromise because of a deadline or other constraint? There are many other factors and so it's unlikely that by creating one design document you will have done enough. Push to do more, the bigger the variety of environments and constraints you have to deal with, the better your eye for complexity and danger will be. In modern iterative environments, there's design activity happening all the time. When someone becomes a senior engineer, we want to know that they can deal with a range of technical and soft skills scenarios.

#### Has done code reviews

It's great, but without the detail of what you taught someone, doing code reviews alone isn't really evidence of effective coaching. If you think that being brutal in code reviews is somehow proof of technical superiority, then you are sadly mistaken. Actual evidence of coaching would be examples of having taught someone something by a review, or by pair programming etc. The key question is 'What did the person learn from you?''  

#### Really good at [CodeGolf](https://codegolf.stackexchange.com)

Now you're just being silly, stop it. However, we can't ignore there are people who think that an ability to create the most convoluted code is somehow a great thing that sets them apart. While of course there are some instances when things are just complicated no matter how much effort you put in, for the most part your code, designs and documentation should be easily consumable and also act as teaching aids themselves.



# Enter Live Operations

So those are a few things that shouldn't be taken as major factors, however as the title alludes to, there is one thing that for me has always stood out as a great indicator of someone's levelling up from junior to senior and that's supporting your own code in production (or supporting other people's too, but ideally your own). There can sometimes be a stigma that support isn't the exciting environment that so many company's marketing materials would have you believe, however with mature modern approaches to iterative delivery, there's no reason that support can't take the form of product enhancement with a prioritised backlog like any other project. Live issues and bugs can be prioritised by a product owner against new / enhanced features in much the same way and in this type of environment, developers will get incredible feedback about what actually makes good code. For example : 

- Maybe that magic framework that reduces dev time by 40% but increases the time for new people to decipher what's going on by 190% isn't worth it
- You'll understand why we should be so strict on not making manual changes once you try and debug or recover a server or environment which has been tampered with in some unknown way. The senior developer knows "I'll just make this change manually for now" is storing up problems for someone else in the future. Once you've suffered at the hands of this yourself, you should be unlikely to ever inflict it on someone else.
- Logs are important, logs that make sense and are easy to follow are the stuff of dreams. Ticking a box by chucking any data you can get your hands on into a log message won't cut it. When an exception happens, think about what data would be useful to understand how, why and what steps might be needed to fix.
 - Less is more. Less moving parts generally makes things easier to understand, maintain and extend. While splitting your service into 60 5-line microservices might seem like the purist approach, if the reality of how they operate is that most can be in a single service then that's the right answer. Knowing when complexity is justified is a key skill in a senior developer's toolbox.
- What's different in production that your local machine? Have you thought about what happens when your code is running in multiple instance behind a load balancer? What impact does that have on how you use state or rely on memory?

Ultimately, every technology decision comes with a tradeoff and operational cost. The senior engineers need the skills to identify, communicate and advise on these. While doing support is also not the silver bullet to becoming a senior, operating your own code is possibly the best singular learning experience you can have so give your junior developers the opportunity, support them and watch them grow!