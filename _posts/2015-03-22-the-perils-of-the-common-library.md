---
layout: post
title:  "The Perils of the Common Library"
description: "Being wrong is a daily part of our lives, learning to recognise and adapt is an important skill to have."
date:   2015-03-22 22:00:00
---

We've all seen it, that place where little bits of code go that we want to use in a few places, the infamous projectName-common. "Stick it in a common library" is often the perceived quick and easy solution and then we can get on with writing the actual sweet sweet application code right? From my experience, having any form of common library requires a tremendous amount of discipline to avoid becoming a dumping ground. Anything that we can't figure out where it should live (or worse, that we didn't have the time or interest in putting much effort into) tends to find it's way into the common bin. We love applying the [Single Responsibility Principle](http://en.wikipedia.org/wiki/Single_responsibility_principle) all over our application code but often seriously neglect our build files and libraries.

A project I worked on recently ended up with a common library with the following dependencies

{% highlight scala %}
"javax.inject" % "javax.inject" % "1",
"com.google.guava" % "guava" % "15.0",
"commons-lang" % "commons-lang" % "2.6",
"org.apache.commons" % "commons-io" % "1.3.2",
"org.slf4j" % "log4j-over-slf4j" % "1.7.5",
"com.fasterxml.jackson.core" % "jackson-annotations" % "2.4.0",
"com.fasterxml.jackson.core" % "jackson-core" % "2.4.0",
"com.fasterxml.jackson.core" % "jackson-databind" % "2.4.0",
"com.fasterxml.jackson.dataformat" % "jackson-dataformat-yaml" % "2.4.0",
"com.sun.jersey" % "jersey-client" % "1.17.1",
"com.sun.jersey" % "jersey-server" % "1.17.1",
"com.sun.jersey" % "jersey-core" % "1.17.1",

"ch.qos.logback" % "logback-classic" % "1.0.10",
"org.mindrot" % "jbcrypt" % "0.3m",
"org.springframework.data"  %  "spring-data-commons"  % "1.5.2.RELEASE",

"org.eclipse.jetty.orbit" % "javax.servlet" % "3.0.0.v201112011016"
{% endhighlight %}

That's quite a mix of purposes going on in there, from jersey server to jbcrypt and spring-data-commons (I heard you like commons so I put commons in your commons so you can common while you common). The things happening in this library were log formatting, filters to attach UUID headers to requests, standard response objects, yaml config readers and a few other completely unrelated functions.

## The Problems

So why would we care?

# Dependency Disease

Anything that wants to use even one tiny part of the common now runs the risk of clashing with a dependency it doesn't care about. I recently came across this problem when trying to introduce a new service using the 0.8 release of the fantastic [DropWizard](http://dropwizard.io/) framework. However because this uses version 2.16 of jersey-server, when I try to use the nice log formatter from common, my new service clashes with 1.17.1 used in the common collection. Frustratingly I don't care about the functionality from common which depends on jersey-server but I'm now blocked because I need to separate out the piece I need. If I now want to extract the piece I need, I might need to go and update all the other services that depend on the existing common. Potentially a lot of extra work for what might have been a trivial change in the first place.

There's another warning here that depedencies do often spread like a disease. The classic 'Copy&Paste' antipattern turns up all too often in build files or 'JustKeepAddingDependencieUntilItWorks'. Adding in potentially thousands of lines of code to an application should be a seriously considered decision.

# High coupling, low cohesion

Low cohesion in that the functions provided by the common library are mostly unrelated to each other apart from their ability to break the test, compilation or functionality of the entire library. High coupling in that our services which use common end up coupled to all this unrelated stuff which may introduce unnecessary fragility and ultimately slow down delivery. This again means that code unrelated to a components purpose can break tests, builds or functionality.

# Higher delivery overheads

When I say overheads, I mean the good ones like integration builds and tests. The more things that get clumped together, the longer that testing and publishing the collection becomes. Suddenly a one line change to the format of a log message needs to test, compile and publish a ton of other unrelated things as well. In this way, we have built a system that slows down development rather the original aim of the common library of speeding it up.

# Mystery Box

What does common do? Is there something in there already for what I need? In many cases the only way to do that will be to read through the packages / namespaces etc. to figure out what is in there. Given that it's already potentially a paste bin that might not even be particularly reliable. In my opinion, reading down a list of properly named repositories, which have a clear purpose, is a much faster and reliable way to see what's already available.

## Separation

Hopefully you've picked up by now that I am advocating, where feasible, avoiding a common code pit in favour of more specific libraries. Unfortunately there is no magic formula to determine exactly where the separations should occur or any nonsense enterprise architect certification that can tell you this. It's down to your own skills applying ideas like single responsibility along with the development and deployment constraints of your own project to come up with the right answer for your needs. However, here are a few questions that might help clarify if code belongs together - 

1) Do these components have any purpose in common? (e.g. a log formatter and a password hashing library probably don't)

2) Do other components, which depend on these, always use all of the functions?

3) Do they only change at the same time?

If you are answering no to them then you should consider if grouping them together is the right approach. By splitting them up you'll end up with more repositories and continuous integration builds but hopefully with the benefit of a more flexible and robust architecture that allows smoother and quicker delivery.



























