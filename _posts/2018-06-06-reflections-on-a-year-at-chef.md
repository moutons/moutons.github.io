---
layout: post
title: Reflections on a Year at Chef
category: posts
tags: chef working customer-support
excerpt: After a year working in Chef Support, I have some things to say.
---
# First Do No Harm

I should start by saying that pretty much everything I have to say in this post applies to pretty much every workplace I've been in, technology or no. I don't intend for this to be a dig at Chef in particular, Chef customers, or any of the Chef community. Any criticism I level is meant to trigger introspection, with the intent to enlighten and improve.

## Context

A little over a year ago I was burnt out on running infrastructure, burnt out on commuting, and burnt out on not being "there" for my family. I'd been working in understaffed on-call situations for roughly 7 years without a break, running greyfield (a nicer term than brownfield, I think) infrastructure without the ability to implement some of the most valuable pain-reducing tools emerging from the devops movement or the C-level understanding and buy-in to effect meaningful culture change. A friend alerted me to an opening on the Chef customer support team, and after some 

## Customer-Facing Teams

This is my first time in something I'd term an engineering role at a product company, and it's been interesting to see how challenging it is to be heard as a customer-facing engineer. I have run the products I'm supporting myself, I've written some Ruby, and I've got an understanding of how product development works. I had understood from the outside that this organization broadly valued agile software development principles, and the learning of half a decade of devops, but have been generally surprised at how difficult it is to get anything other than clear and obvious bugs in code acknowledged by product teams.

I know that a lot of this comes from the competing priorities of business making money in a pre-IPO startup vs genuine concern that customers have a good experience with useful software, but it's still been surprising.

My experience so far has shown me that if anything, the experiences of customer-facing teams are undervalued. On the support team, we see critical issues in implementation weekly. I've talked with the engineers who work closely with a smaller set of customers for longer periods of time, and they often call out areas in which the on-the-ground implementation of our kit doesn't mesh particularly well with what I understand is the "intended use" patterns when I talk with the folks I conceive of as product owners. I think it'll be interesting to try and work towards improving that gap in understanding, if I'm allowed to. More on that later.

## Walk Like a Duck

Another thing I'm learning is to give a little more credence to what my unconscious mind is telling me about an interaction. The pattern-matching that served me well as an on-call web operations type does a decent job of telling me when a customer inquiry is actually urgent and when a ticket submitted as high-priority isn't actually particularly urgent.

It's interesting to develop ways of handling "YYY is absolutely critical, please fix this now" tickets where little detail which would help you troubleshoot a problem is provided, where the folks on the team seem to have an understanding that there's often not a real desire on the part of the customer to work towards a solution themselves. That's interesting, because Chef is a pretty open framework that can be adapted for many uses and often more detail is absolutely required in order for any kind of work towards resolution is performed. Many support tickets involve standing up test environments where we replicate what the customer is doing in their own environment so that we can try to see ourselves where things are breaking, and either recommend configuration or code changes at the customer site, or recommend an update to a Chef product based on the error we find.

If it walks like an issue that is not particularly urgent and quacks like an issue that isn't particularly urgent, maybe it's not particularly urgent.

## Silos

Back to the point about organizations integrating the things they've learned from years of doing the devops, it's staggering to me how little alignment there is here as to what we're working towards and why. Customer-facing teams themselves aren't particularly well aligned - support and account portfolio (we call this practice Customer Success) teams are barely in regular communication about customer issues, sales teams regularly toss issues encountered prior to a support contract being signed over the wall, the aforementioned divide between customer-facing teams and product, it's amazing to see how much opportunity there is to come to alignment on what I would have thought were pretty straightforward easy wins prior to being on the inside.

Given my prior experiences in ops and trying to learn about silo-busting, I'm a little disappointed not to see more progress at a place like Chef. Nevertheless, it's a good lesson in people pretty much always being people and reminder that none of this is actually particularly easy. Maybe more of this was implemented at some point and as the organization grew silos formed again. Maybe the grass really ever is only greener on the other side. At least the people are by and large wonderful, none of this should be taken to mean that I don't appreciate working with this team and these folks regularly and that I get any kind of sense that people don't mean well and aren't trying.

## Wrap It Up, B

Ok, that's about it for this summary. I've meant to come up with retrospectives on workplaces before and it's nice to feel like I can do that here. Hopefully I'll be able to keep this up. Cheers and hugops!
