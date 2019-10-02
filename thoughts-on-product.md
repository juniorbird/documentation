# Thoughts on Product

Product's goal in an Agile environment is to both drive work forward and minimize risk/waste at each step. 

## Driving Work Forward

Work is driven forward by collaborating with stakeholders, and helping those stakeholders articulate real business needs. Often, these are needs the stakeholder didn't even realize they had.

A major risk for Product is that they become simply a turnstile: a hurdle the stakeholder must cross to get work to progress. If that's the case, the stakeholder will jump the turnstile and bypass Product. Product must add value, not only by being the team member with people skills, who can communicate between client and engineering, but by helping all stakeholders articulate, prioritize, and act on needs.

It's tempting for Product to not consider Engineering to be a stakeholder, but wrong. Over the long term, excessive tech debt or other Engineering weaknesses will block achievement of business goals, up to and including preventing the business from working at all. Product's role is both to be a partner with Engineering in completing work, and to appropriately prioritize Engineering goals.

## Minimizing Risk & Waste

The obvious kinds of waste are work not put into production, or dev resources idled. But it's easy for Product to waste work earlier up the process chain. Excessive work put into a product before it's proven that the product is desirable to stakeholders, or that it can meet those stakeholders' needs, is equally wasteful. Product can minimize that kind of waste by:

1. Prototyping with paper or low-fi wireframes early, and validating user satisfaction; business needs met; and engineering feasibility, in at least a basic way, with just a few days' work on any given featureset.
2. Going to Design/UX to make more mature versions of those wireframes, progressing to complete mock designs. As these wireframes are fleshed out, they can be tested again, and even have various configurations A/B tested through a manual process. This will provide ongoing work validation. Features that aren't actually useful to key stakeholder groups will not survive this step. 
2. When featuresets are relatively fixed but design/UX is still under development, Product can begin working with Engineering to size sub-epic chunks. This will help Product validate that the size of work will be justified by the stakeholder benefit. 
2. If the size of work is appropriate, Product and Engineering should collaborate to split user stories up into clear and actionable JIRA tickets, each of which is a complete, deliverable unit of work. Often, back-end work can be started at this point, making it easy to begin frontend work when design/UX is complete. In this way, rework can be minimized and scope can be effectively ballparked, early.
2. Once frontend units of work begin becoming complete, they should be validated with stakeholders. The goal is to deliver work in small chunks, so that the team can be sure at each step that the work product meets stakeholder needs, and that the project is moving forward in a way that creates real business and user values. This also makes it easier to stop down and revise already-done work if a just-completed work unit doesn't pass validation hurdles.

Rough out features early; design and dev in parallel as much as possible; always be validating; integrate late.

## Workflow

This drives a workflow looking something like this:

!Slide1.gif|border=1!

## Writing Good Stories

Stories should almost always use the format "As a <user type>, I want to <do action>, given <state dependencies>, in order to achieve <actual goal>." This is to make Product's job easy:

* It's possible to be exhaustive with needs
* It gives a chance to validate goals with actual users
* It's possible to validate user types with actual users
* Different actions should usually be different tickets
* Different state dependencies should usually be different tickets
* Different user types should usually be different tickets
* It removes engineering assumptions from tickets, allowing engineering to complete the tickets how they see best

A ticket like this is easy to t-shirt size at this stage.

Once Product has a t-shirt sized ticket they plan to proceed with (or a small ticket that doesn't need t-shirt sizing), they can then add specifics, including things like:

* Known **edge cases**, and how to handle them
* Any **tracking variables** or other calls to third party scripts that the engineering team shouldn't be expected to know
* **Copy, links**, etc.
* Key **SMEs** outside the Engineering team that the dev should reach out to
* Descriptions or animations of *interactivity* that are beyond the basic behaviors of browsers
* Any **files**, logos, fonts, etc. that need to be uploaded
* Apart from that, all **design** requirements _should come from comps, wireframes, etc_ that are _linked from the ticket_.

With all of this information, the dev team will easily be able to size and pull in the ticket.

## Handling Epics Well

The workflow above is useful for all tickets, but primarily oriented towards larger epics. The challenge with epics is to both push forward, and not get bogged down in details too early. The epic should be validated first, then the stories within the epic. (If the epic isn't desirable, best to not expend effort on the stories!)

Once the basic wireframing work has been completed for the epic end product, the Product Manager can begin to write out user stories in the basic format above, without detail. Those user stories can then be t-shirt sized, leading to a ballpark size for the epic.

If the epic proceeds, the t-shirt sized stories are given some detail, as described above, but do not have to be written in complete, final detail yet. Those stories should be taken to the dev team for epic sizing, a special sizing meeting. The goal of this meeting is to size as much of the epic as possible. If it's not going to be possible to size the whole epic, consider breaking it up into sub-epics. This meeting will also unearth dependencies within the epic work. It's not unusual that a meeting like this will reveal new stories, and if new stories do appear it shouldn't be seen as a failure by anyone. Instead, it's a success: rather than having surprises later that may threaten the epic, more is learned now.

One great way to handle this is to set up a wiki for the epic from the get-go, and build it out with content and links at each phase. Ultimately, the wiki will be a great reference for developers and users of the epic feature. I put up [an example of such a wiki I made here](https://juniorbird.github.io/product-wiki-example/). 

When stories are sized and dependencies are set, then they can be placed in the appropriate priority in the backlog. 

## Building Good Sprints

Sprints generally contain 3 types of stories:

1. Epic work
2. Bugfixes
2. Pickup stories

Think of an engineering team's sprint capacity like a jar that you want to fill with stones of various sizes. First you put in the large stones, and see how much space is left -- these are the epics. Then you add smaller stones, to fill in the spaces between -- these are the bugfixes. Finally, if there's space, you add sand -- these are the pickup stories. Sometimes sprints will never contain the big stones, but rarely if ever can you fill a jar without small stones and sand.

### Epic Work

This is the kind of work that comes from the complex process above. The amount of epic work that can be taken on in a given sprint is determined by dependencies within the epic. It's rare that an epic can be completed in 1 sprint.

Normally, this work will be 0-50% of the sprint. If the epic work goes over 50%, it's unlikely the team will be able to address both of the other kinds of work.

### Bugfixes

Because humans are fallible, there will always be bugs. These most often come from development errors, missed interactions within the tech stack, missed requirements, and missed interactions within requirements.

Normally, this work will be 15-25% of the sprint. At least 10% of the sprint capacity _must_ be kept aside for emergent bugs. If less capacity is kept aside, it's unlikely any prod bugs will be addressed during a given sprint.

Devs generally don't love working on bugs, but all devs love a good hardening sprint, where of bugs and tech debt are wiped out. If there are too many bugs, consider an explicit hardening sprint.

### Pickup Stories

These are stories that aren't associated with an epic. Sometimes they're really important and impactful; other times, they've been sitting around in the backlog for a while and finally made it to the top. Ideally, these are smaller-sized stories that can be used to fill in the nooks and crannies of capacity.

Normally, this will be 15-85% of work. Under 15% and you're usually idling devs; over 85% and see the issues with bugfixes. 

Many sprints are all pickup stories and bugfixes. This is fine.


## Building a Good Backlog

A backlog is, at the core, two things:

* A work queue that ensures that expensive developers are never idled
* An expression of short- and medium-term corporate priorities

The queue part is pretty obvious: 2-3 complete sprints should be ready at all times, not just to prevent idling but also to make it easy to talk schedule with stakeholders.

The priorities are a little more complicated, but it comes down to the two kinds of work a Product Manager must do to keep a backlog filled:

1. Identify and ticket up emergent needs that have to be worked within the next 14-60 days
2. Turn larger strategic initiatives into epics and stories, to meet business requirements 90-365 days out.

Unless the Product Manager does _both_ of these, they'll ultimately fail. If they fail at #1, the dev team will inevitably be idled and both the PO and select devs will be let go. If they fail at #2, they won't deliver business value and everyone will be fired. No pressure.

Periodically, the backlog should be groomed, because only 3 things can happen with an old story, and they're all bad:

* The story can sit there and hide more useful stories, as a haystack hides a needle
* The story can be worked and turn out not to be relevant, and then precious dev capacity will be wasted
* The story can be not worked, and then turn out to be important, and then at best you get yelled at

Do all the above, and people will actually look at the backlog all the time, because looking at it makes them feel empowered in their work lives. 

## What is Product Responsible For?

Sometimes, it's not clear what team owns any given part of the process in the company. Here's what Product owns:

* Everything

Once again, no pressure. 

Let's break it down. Product owns, at the very least:

* Stakeholder management, because who else can do that? This involves both understanding needs and keeping stakeholders updated. If a stakeholder is, or doesn't feel, listened-to; or feels they don't know status; that's the PO's problem.
* Prioritization, because if the right things aren't done at the right time, might as well do nothing ever.
* Architecture, because if the project can never be completed, then everyone gets fired
* Architecture again, because if the project is done but it's not possible to iterate on the work and continuously improve, everyone will be swamped with rework and you'll have to explain why past work turns out to have no value. Especially if you capitalized it!
* Project Management, because if the project is never completed, then everyone gets fired
* Training, because if internal users don't adopt the new feature, it's a failure, no matter how perfectly it was implemented
* Marketing, because if external users don't adopt the new feature, it's a failure, no matter how perfectly it was implemented
* Launch, because if the new feature doesn't get out there right, look good, and get used immediately, it's a failure, no matter how perfectly it was implemented

You may think that other people own some of these. Nope! That's the difference between being _responsible_ and _accountable_. Engineering, Project Management, Sales/Client Management, Publishing, Executives -- they all have things they're _responsible_ for. They even may be _accountable_ for these things. But you are the only person who is _accountable_ for all this! And yet you can only push things in the right direction, not actually make them happen. Lol.

### Product Responsibility in Stories

Just as an individual dev is accountable for building the feature described in a ticket, an individual PO is accountable for that ticket being a good description of the feature. If code is delivered, and fulfills the requirements, and works, but does not actually fulfill the needs of the feature, the ticket has been completed successfully. The dev and PO need to coordinate to determine the scope of work for any missed requirements, and break them out into another ticket if the scope is anything above trivial.

The same is true for QE: requirements need to be sufficient to be testable. If gaps are identified in testing, then QE, PO, and dev need to work together to determine solution as above.

## How to Be A Successful Product Manager

It's easy! 

* Always get up and talk to people
* Never have a meeting without an agenda
* Always follow-up with every meeting and conversation with some sort of written record
* Keep notes on yourself at all times
* Voluminous wiki-ing, so that, once you've determined something, other people can bother the wiki and not you to find it out
* Block out work time, don't let meetings take over your life
* Call people on their bullshit early, but don't be shy to bullshit them
* Never bullshit thyself, however
* Don't take responsibility for a thing unless you're actually responsible
* Protect your engineers from your stakeholders and your stakeholders from your engineers

All of this is why I am not a Product Manager anymore, and also probably why I like Scotch. Good luck!
