Twisted Logic: Endpoints and Why You Shouldn't Be Scared of Twisted
============================================

**Presenter:** Ashwini Oruganti

**Track:** III

**Description:**

This talk will be a survey of my learning experience adding new endpoint APIs
to Twisted, an event-driven networking engine (as a Google Summer of Code
project), with a special focus on the analysis of some of the horror stories
that surround Twisted. Right from the asynchronous I/O model to Deferreds: if
it scares you, we’ll figure a way out and see what the makers of Twisted say
when confronted.

    https://us.pycon.org/2013/schedule/presentation/40/

Endpoints
+++++

Standardized APIs for connecting clients and listening for requests.

Example::

    endpoint = TCP4ServerEndpoint(reactor, 8007)
    endpoint.listen(Factory())

**It's Just Code**

The Moral
+++++

* Don't get flustered
* Don't overthink
* Forget it's Twisted

Read the code -> Solve the Problem

Callbacks can be confusing, and difficult to debug.

It's very complicated, it's even in the name (Twisted).

Part of the problem is that the idea of the Twisted framework is foreign, it's
different than the other frameworks that we use (django, etc).  But you're
using Twisted because it has something that the other alternatives don't have,
so even if the ideas around the framework are different than what you're used
to, you know why you need it, so you have a frame of reference, you just need
to lean on that.







