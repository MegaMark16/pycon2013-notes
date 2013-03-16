Making DISQUS Realtime
===========================

**Presenter:** Adam Hitchcock

**Track:** II

**Description:**

What does it take to add realtime functionality to a truly web scale app. The result is the DISQUS realtime system, a highly concurrent system for allowing web clients to subscribe to arbitrary events in the DISQUS infrastructure.

    https://us.pycon.org/2013/schedule/presentation/46/

DISQUS
+++++

People are more engaged when things happen in real time.

They get a lot of traffic, over a billion hits per month.

They call it RealERtime.


They use:

* Thoonk
* Redis
* pub sub
* nginx

Real Time Progression
+++++

Old system was memcache pulling every 5 seconds.

New system is redis pub/sub and a Flask proxy cluster.

They quickly ran out of CPU on the Flask servers, so they moved things to a
backend server to handle formatting.

This was better, but the Flask servers were still growing too quickly.

Replaced Flask servers and HA Proxy servers with an Nginx pub endpoint.

Thoonk
+++++

The Thoonk queue takes post_save and post_delete hooks, sits on tops of Redis.

Provides job semantics (what's claimed, what's not)

Gevent
+++++

Gevent is the best thing ever, it lets you process things really fast.

Works with pipelines and mixins to compartmentalize logic.

Data pipelines using mixings (each mixin manipulates the data and passes it on).

Nginx is Great
+++++

Replaced webservers and redis pub/sub

    http://wiki.nginx.org/HttpPushStreamModule


**EventSource** Lets the browser handle the async calls instead of making
javascript do it.

Testing
+++++

**Darktime** - Use existing network to load test, pull out a certain percentage of
your user base at the new code.

**Darkesttime** - Testing a single instance with a ton of traffic.

**Measure everything** - Especially when numers don't match up, even if it's
hardin a distributed system, and try to express things as +1 and -1 if you can.


When the pope was announced they saw over 6TB of traffic that day.

Lessons
+++++

* Do hard work early
* End-to-end acks are good, but expensive
* redis/nginx pubsub is effectively free
* Greenlets (gevent) are free too

Also
+++++

Check out HttpPushStreamModule!!!

