So...I want to monitor some stuff
=================================

Possibly __the__ most common way I tend to see this question happening is someone asking "how do I monitor my (web site|DNS server|router|internet connection)?", and the question ends up being a form of the [XY Problem](http://mywiki.wooledge.org/XyProblem). What I mean by this is that the question isn't exactly _wrong_, as much as it is a misunderstanding of the actual problem at hand. Some more momentary contrivances:

 *  "I want to monitor my web site"

    This question could actually be quite loaded. The asker might mean they want to track how many people are visiting their site, or they might mean they want to know whether the server itself isn't serving up the site anymore. They might even mean they want to monitor the content, perhaps for comment spam, or the occasion of the site software getting hacked. In all of these cases, the question as it stands is not _good_ for the purposes of communication the actual intent, and some further questioning would first have to go about. Being clear about your requirements, from the getgo, would help you understand better from which angle you want to start.

 *  "How do I monitor my database server?"

    Another common question, the meaning of which can also be quite varied. "My database queries/writes are slow, how do I figure this out?" might be what's actually meant, or perhaps you want to know how many transactions/queries you're doing (perhaps along with how speedily you're getting your results).

 *  "Is anyone in the office downloading anything at the moment?"

    Perhaps someone is, without them knowing it! Some updates, for instance, can often run in the background without notifying the user (or without the user noticing). Email clients syncing a large mail down in the background, or your phone starts uploading photos the moment you connect to office wifi network.

In all of these cases, a better understanding of the problem at hand already goes a long way to answering your question, and thereby also narrows the possible field of solutions you actually need to look at. Which brings me to the next point:

Identifying what you need to monitor
------------------------------------

There's a sort of golden rule in the UNIX world, when it comes to tasks: "You only ever type a task out twice. The first time when you figure out how to do it, the second time when you automate it." It's such a popular notion that there's often pride taken in how good one's scripts might run (where good is measured in various ways, including speed, safety, cleverness, ...), up to the point where people make [graphic illustrations](http://imgur.com/gallery/Q8kV8) to point out why it's a good idea.


