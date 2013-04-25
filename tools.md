Musing on tools
===============

There's a quote I once read somewhere, and it went thus: know your tools well enough to know why they suck. It's almost a variation of [The 3 Stages Of Learning](http://c2.com/cgi/wiki?ShuHaRi). To steal an example from [@eevee](https://twitter.com/eevee), in the beginning you could bash nails in with a rock, but you later learn that it's not really the best model for getting nails into things (and that hammers exist). In much the same way, monitoring tools are vast and varied, and thus far you usually only know which does what when you've paid your dues to get to know them.

There is, of course, no substitute for experience. And each environment is also unique. This is why there is no one-size-fits-all approach to monitoring. Your application might just run on people's windows workstations at a pace any desktop user is comfortable with, while your neighbour has an application that needs to regulate the traffic lights for a whole city, a scenario where even the slightest timing issue could be the cause of significant damage (and even loss of life). So while experience is certainly a key requirement for you to be successful in your mission of monitoring something, I hope that this guide can be a worthwhile addition to the process.

Distinctions
------------

When you start searching for software to do monitoring, you'll find a lot of things that are called **Network Monitoring Systems**. I personally feel this is an overly vague term, and would like to clarify the distinctions between the various common parts of monitoring which you'll run into.

**Trending**: these are systems like MRTG, Ganglia, Cacti, etc., whose purpose it is to collect metrics (and usually display them too). In general these systems are also _passive_, in that they don't react to events.  
**Synthetic/active monitoring**: these are systems that are actively pinging and connecting to systems, often even simulating protocol interaction to ensure that your services are still alive. Examples of these systems are Nagios, Zenoss, OpenNMS.  
**Events**: these are deviations from the norm. Common examples are syslog messages, SNMP traps, BGP session loss, network cables being bumped out, server daemons falling over. Effectively, any /specific/ thing you can point to as a bump in the wire (note that I do not point them out to be fatal).  

Each of these types of systems have various moving gears available inside, and different primitives which they build on. A common tool you may be familiar with/have heard of is _rrdtool_. Its claim to fame is that it will never have a datastore grow beyond the size it gets made at (it's also in the name: "round robin database"). It also has builtin graphing, aggregation, and a bunch of other stuff. At the same time, it has a fairly unwieldy syntax to a beginner. Another way to do a similar thing would be to use something like flot or highcharts, perhaps even gnuplot, combined with a time series database like opentsdb or whisper. In rrdtool, you get all of it in one tool, while in the latter you get to glue the pieces together yourself. Both have their advantages and disadvantages, and an understanding of this will help you better choose the one suited to your needs. At the same time, not understanding these points may cause days or weeks of frustrating dev, trying to hammer a system into a shape it was never designed to be.

Flavours
--------

Most of the pre-packaged systems like this are typically oriented strongly towards either _systems_ or _network_ monitoring. The reason I make this distinction is because, beyond a certain point, the "network" is not just a LAN on a switch. In any mid-size business you may already run into this situation, where you have two or more different internet providers, each supplying their own CPE (Customer Premises Equipment) to do the service handoff to your network. And with this you may have traffic balancing, or you may consider one circuit a backup should the main one fail. Even just this basic scenario already calls for _trending_ and some measure of active monitoring or event awareness. An example of this would be as follows:

 *  __Trending__

    You may wish to keep track of the utilization on each link, to measure whether you are regularly near capacity, or using more data each month than a metered connection may allow for.

 *  __Active monitoring__

    In either a load-balanced scenario or that of a master+failover setup, you would benefit from knowing whether each link is alive or not. If any link drops, you could react to it appropriately. Not knowing that your primary has gone down, then ending up on a backup circuit (perhaps even a smaller one, because "it is only the backup, after all"), would leave you instantly vulnerable to downtime should the backup link itself also go down at the same time.

 *  __Event awareness__

    This one, by itself, is similar to active monitoring. In fact, active monitoring is often the likely _trigger_ or _creator_ for an event (although there are many cases where it might not be), and is another form of event that you could react on quickly.

"But," you might be thinking, "couldn't that link fail often? What if we wanted to track that?" And you would be correct if you _did_ think so! We can feed events back into our _trending_, and build up a uptime/fault history. This is often required in various forms of service delivery, and having the information on hand without a large amount of effort could be invaluable.

This, of course, is just a fairly basic example for the purposes of illustration, and it can get _far_ more involved (think of the monitoring operations which happen at the scale of Google, Facebook, or Akamai!), but it suffices as an example of a _network_ being monitored. Conversely, _systems_ monitoring would be like keeping track of your webservers, how much spam your mailservers are bouncing, whether all machines in the network are running all the services they should, responding in reasonable times, and so much more.
