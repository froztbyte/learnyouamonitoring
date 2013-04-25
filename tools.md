Musing on tools
===============

There's a quote I once read somewhere, and it went thus: know your tools well enough to know why they suck. It's almost a variation of [The 3 Stages Of Learning](http://c2.com/cgi/wiki?ShuHaRi). To steal an example from [@eevee](https://twitter.com/eevee), in the beginning you could bash nails in with a rock, but you later learn that it's not really the best model for getting nails into things (and that hammers exist). In much the same way, monitoring tools are vast and varied, and thus far you usually only know which does what when you've paid your dues to get to know them.

There is, of course, no substitute for experience. And each environment is also unique. This is why there is no one-size-fits-all approach to monitoring. Your application might just run on people's windows workstations at a pace any desktop user is comfortable with, while your neighbour has an application that needs to regulate the traffic lights for a whole city, a scenario where even the slightest timing issue could be the cause of significant damage (and even loss of life). So while experience is certainly a key requirement for you to be successful in your mission of monitoring something, I hope that this guide can be a worthwhile addition to the process.

Distinctions
============

When you start searching for software to do monitoring, you'll find a lot of things that are called _Network Monitoring Systems_. I personally feel this is an overly vague term, and would like to clarify the distinctions between the various common parts of monitoring which you'll run into.

**Trending**: these are systems like MRTG, Ganglia, Cacti, etc., whose purpose it is to collect metrics (and usually display them too). In general these systems are also _passive_, in that they don't react to events.  
**Synthetic/active monitoring**: these are systems that are actively pinging and connecting to systems, often even simulating protocol interaction to ensure that your services are still alive. Examples of these systems are Nagios, Zenoss, OpenNMS.  
**Events**: these are deviations from the norm. Common examples are syslog messages, SNMP traps, BGP session loss, network cables being bumped out, server daemons falling over. Effectively, any /specific/ thing you can point to as a bump in the wire (note that I do not point them out to be fatal)


