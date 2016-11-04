---
layout: post
title:  "BSIMM - Building Security in Maturity Model"
description: "An introduction to the Building Security in Maturity Model"
date:   2016-11-04 - 13:00:00
---

I recently attended a talk by [Nick Murison](https://twitter.com/nickmurison) from [Cigital](https://www.cigital.com/) covering 'Security in Agile'. I must confess to being a bit cynical beforehand as most talks about 'Doing X in Agile' (where X = Performance, Security, Accessibility etc.) could be summarised as 'Do it continuously, early, and automate as much as possible'.

I was pleasantly surprised to find this was much more useful than that. There were some useful tips on security user stories, or adding security stuff to your existing stories if that works better for you, which you can take a look at through the [slides here](http://www.slideshare.net/Cigital/agile-security-68073294). As well as this, Nick was talking about BSIMM which, full disclosure, is a thing that Citigal created / are involved in.


## BSIMM

According to the [BSIMM site](https://www.bsimm.com/about/) :

"The Building Security In Maturity Model (BSIMM, pronounced “bee simm”) is a study of existing software security initiatives. By quantifying the practices of many different organizations, we can describe the common ground shared by many as well as the variation that makes each unique.

BSIMM is not a “how to” guide, nor is it a one-size-fits-all prescription. Instead, BSIMM is a reflection of software security.""

So it looks to be in the same vein as the [Puppet State of DevOps report](https://puppet.com/resources/white-paper/2016-state-of-devops-report) in that it is a description of what is currently happening rather than a 'Do this and you have all the security'. The most recent version can be found [here](https://www.bsimm.com/download/)

The core of the framework itself is broken into these 4 domains

#### Governance: 
Practices that help organize, manage, and measure a software security initiative. Staff development is also a central governance practice.

#### Intelligence: 
Practices that result in collections of corporate knowledge used in carrying out software security activities throughout the organization. Collections include both proactive security guidance and organizational threat modelling.

#### SSDL Touchpoints: 
Practices associated with analysis and assurance of particular software development artifacts and processes. All software security methodologies include these practices.

#### Deployment:
Practices that interface with traditional network security and software maintenance organizations. Software configuration, maintenance, and other environment issues have direct impact on software security.

Each of these domains is then further broken down into 3 practices which then contain specific activities. Based on the amount of organisations doing each activity, it is ranked in the maturity model. So basically level 1 is 'Most people are doing this' and level 3 is 'hardly anyone is doing this'.

# Things I like about it

Having taken a read through the report, there are a few initial things that I think justify looking into this further

- It's easily digestible. Sounds simple, however reports of this nature can be very dry and abstract whereas this one is clearly broken down into useful sections and the data aggregation graphics are (mostly) useful rather than just eye candy
- It's very open about being an observation rather than a recommendation. There can be a temptation with things that look like checklists for people to take them as a comprehensive guide / silver bullet. That's not what this is and it doesn't pretend otherwise
- As an annual report, it can show difference over time which can be a useful indicator of trends. Obviously you need to judge for yourself if you think the organisations involved are likely to set trends that are worth following or avoiding.
- The list of companies involved builds confidence in the data. There is a decent spread of types and sectors from huge banks like HSBC to more recent tech focussed companies like Box.
- The scoring is laid out in such a way that you can apply it to your own organisation. While this sounds simple, leaving it open and low friction is a massive help to adoption as opposed to guarding it behind paid consultancy

So based on an initial read through, I think this is worth the time to complete against your organisation and added to your ongoing security practices, both from the actual activities themselves and from the description of what effective security groups in organisations look like.

