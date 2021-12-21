---
layout: post
title: Tool Choice in an Organization
category: posts
tags: working tools conways-law
excerpt: Tool choice can reveal things about an organization, ignore this at your peril.
---

## Primo non nocere

These observations are based on my own experience using tools to perform primarily web operations work in technology organizations, and somewhat less on my experiences using technology as part of social services work, banking, and other work prior to working primarily in technology. I do name specific tools and give my own opinions, which do not reflect all possible experiences with those tools. If your experience differs and you'd like to discuss that, I'd be happy to hear from you. I do not mean to share these opinions to dig at the people who are working on them, and hope that I can be afforded the understanding that any criticism I level is meant to trigger introspection, with the intent to enlighten and improve.

## F this thing in particular

After having recently worked folks with many organizations in a vendor capacity, and long ago sone something similar as a consultant, I believe that it is true that you can say that some tool choices reveal things about an organization. Not as in "every time you see X being used within an org, Y is true about that org" but as in "where you see an organization using X, it's worth examining to see whether some aspect of Y is true within that org".

## People like different things, this is what I think I like

Not everyone wants to work the same way, and not everyone wants to accomplish the same sort of things at work. All workplaces deal with the chaos that is human beings working together. All people go through changes in their lives where they want different things from themselves, from their work, and from their coworkers - therefore it's not reasonable to say that "it would be best if every organization adopted Y practice and/or improved their Y practice" (with the possible exception of value things like "we should respect each other").

In no order, I believe these are the sort of things I value in a workplace:
* Responsibility towards society as well as money for shareholders
* Enablement of IC Autonomy
* Senior Leadership balances Ownership of the culture and Accountability towards employees
* Coworkers work towards frankness and mutual respect
* Learning Organization practices (a la Donella Meadows, Peter Senge)

## Frustration

When comparing a the history of a commercial source control tool like Bitbucket to competitors like GitLab, GitHub, and even Perforce, it becomes evident very quickly that Atlassian didn't continue to develop Bitbucket in the same way their competitors did. Ask a developer who's worked on a sizable codebase what they think of [the "Considerations" section here](https://confluence.atlassian.com/bitbucketserver/bitbucket-search-syntax-814204781.html). To clarify, in order to search for occurrences of explicit strings such as `repo.Status == RepositoryBroken` one would have to clone down every repo in the organization locally and perform a search on the filesystem.

When encountering an issue where one's work is obstructed by the lack of functionality which has become table stakes in a core application, a developer becomes frustrated. "Why do we use something which doesn't provide me with this basic quality-of-life feature? Why do I have to waste time asking people if they know places where we're using a string which is cropping up in this error message so I can ship my feature?" we ask. When we don't receive satisfactory answers, we might initially dismiss the frustration. As such incidents accrue, we might try to advocate for the use of a more suitable tool, or to investigate ways in which we can supplement the basic function of our employer's tool of choice (and thereby incur technical and process debt). If our efforts to acquire a suitable tool fail, we might begin to look for other jobs, or normalize a less engaged attitude towards work. "If they don't care enough about us to make sure we have the tools we need to get our job done without unnecessary friction, I don't see why I should bust my butt to ship code" we might say.

Search isn't the only place Bitbucket falls short of its competitors, but this is a good example of why it's on my list of red flags when considering taking a position at a company.

Inter-team chat has been transformed by Hipchat (RIP) and Slack. Chat tool makers scrambled to implement features like ad-hoc room creation, threads (controversial), reaction emoji, APIs to enable interaction with other tools from chat, and while there's tons of fun and money in the banana stand there's some clear ways in which chat tools can obstruct work. Search, again, is a big one - when your organization's chat tool of choice doesn't implement search well, that means conversation and knowledge shared in chat is lost to folks who need it: your account teams can share tips and tricks but new folks who join 12 months later won't benefit unless that knowledge is distilled elsewhere (Confluence? search stinks there too). Your support teams can't find a discussion among the developers from back when the product was being worked on which helps them see exactly where to look for a solution/create an Issue requesting a bugfix.

Microsoft Teams might seem like a no-brainer - it's got some of those features I mentioned above! However, in practice they're poorly implemented and you'll quickly find working in large groups is frustrating. Search offers KQL to search messages `From:Person's name` but in practice you'll find yourself issuing a DM to Stephanie saying `approver group` instead of searching for that string. Speaking of KQL, it's probably very neat to SharePoint admins and folks working on DLP/legal discovery that it's there but I feel like I'm being offered JQL. 

## Closing Thoughts

I have a decent understanding of the immense weight of privilege which these words rest upon, and yet I will write them anyhow:

By and large, we make an absurd amount of money for the companies which employ us. It's not too much to ask that they provide us with tools to perform our job that are not demonstrably worse than their competitors. There are alternatives to all of the tools I've discussed which sit somewhere in the middle of the Slack/Teams or GitHub/Bitbucket divide both in function and in price, and it's really not asking much that our employers spruce up our work environment a bit. Until the Truffula trees run out, we should all get Thneeds to wear as we're doing the Onceler's work.
