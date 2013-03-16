Messaging at Scale at Instagram
===========================

**Presenter:** Rick Branson

**Track:** II

**Description:**

As activity accelerated from just a few thousand activities per day to hundreds of millions, Instagram needed a reliable, scalable messaging infrastructure to distribute work and messages. In this talk, I'll jump from a crash course in the abstract concepts of queueing into the implementation details & hard-earned know-how from experience building massive-scale Python-based systems.

    https://us.pycon.org/2013/schedule/presentation/106/


Trying to get photos for friends of friends is expensive.

You should try to get out of the request ASAP.

Justin Beiber effect: Hundreds of thousands of followers.

Gearman & Python
+++++++++++++++++

* Persistence is slow
* Ran out of memory
* Pulling based, so workers pull
* Should have used Redis


Celery
+++++

* Fast
* Great Python support
* celeryd to keep things going

RabbitMQ
+++++

* Not as fast as Redis, but reasonably fast
* Mirrored broker nodes
* Over previsioned so they can burst up to higher capacity

Alerting
+++++

They use Sensu (Ruby)

Graphing
+++++

Graphite and statsd

Brokers
+++++

They use a round robin boker approach

Performance
+++++

* They push about 4,000 tasks per second
* ~25,000 app threads publishing tasks

Why They Chose Celery
+++++

They cna get new engineers up to speed quickly

Scaling Out
+++++

* Back in the day Celey only supported 1 broker host
* They created kombu-multibroker

Gevent
+++++

Only some of their tasks run on gevent, some are on multiprocessing mode.
Celeryd_multi allows running tasks in different worker modes.

They us Gevent for anything network bound, and anything that needs network
bound functionality and local actions they split it up with callbacks.

Problems
+++++

* Slow tasks monopolize workers
* Running higher concurrency is inefficient
* Lower batch size is also inefficient

They isolated their feed delivery, because anything that you don't want to get
backed up by slow tasks should be on its own worker.

They have three concurrenc levels

* Fast
* Feed (important)
* Default

They start new tasks out in default and then promote them to Fast as they prove
themselves to be fast.

Failures
+++++

It's impossible to determine whether a task has died or is just really slow, so
it's important that tasks be idempotent so thta you can retry.

You need acknowledgements for when tasks finish successfully.

They only pass self-contained, non-opaque data  as arguments to tasks.

Tasks should execute within a few seconds, otherwise restarts take a long time
and they gum up the works.  They use a soft time limit of 20 seconds, and a
hard time limit of 30 seconds.

Future
+++++

* They'd like to get better
* Utilize results storage and other celery features they aren't using now
* Single cluster for control queues, becuas they're breaking all the management
tools for Celery right now
* Eliminate their multi-broker shim (kombu-multibroker) now that celery
  supports multiple brokers
