Python Profiling
===================================================================

**Presenter:** Amjith Ramanujam

**Track:** II

**Description:**

This talk will give a tour of different profiling techniques available for
Python applications. We'll cover specific modules in Python for doing function
profiling and line level profiling. We'll show the short comings of such
mechanisms in production and discuss how to do sampled profiling of specific
functions. We'll finish with statistical profilers that use thread stack
interrogation.

    https://us.pycon.org/2013/schedule/presentation/86/

cProfile
+++++

Python - Batteries Included.  It comes with its own profiler, **cProfile**::

    python -m cProfile my_scripy.py

Sometimes you get a ton of output, so you should save the output to a file::

    python -m cProfile -o file.prof my_script.py

RunSnakeRun is a GUI interface for analyzing profile files created with
cProfile.

A Catch
^^^^^

Using the profiler adds overhead to your code, and it runs slower, so you don't
want to run the profiler in production.

**It's slow**

So you could only profile critical functions by using a decorator to start the
profiler at the beginning of the function and turn it off at the end.

Most likely your critical functions are the ones you wnat to be fast, so you
don't want them being profiled all the time.

Statistical Profiler
+++++

Kind of like an Overly Attached Girlfriend.

Interrupted - "Hey"
Inquired - "Where are you?  What are you doing?"
Collate - "You don't love me anymore!"

This all has overhead.

Inquire: Stack frame of every thread, every 100 ms.::

>>> import sys, traceback
>>> frames = sys._current_frames()
>>> stack = traceback.extract_stack(frames)

**StatProf** Uses unix signals and the CLI to profile stack traces.

**Plop** Uses unix signals with a callback.

X-Ray Sessions
+++++

Was secret, but now it's in beta.  What it does is, you can pick a specific
page and you want as much information as possible.  You can run an x-ray
session on that page and they will collect the first 100 traces (transactions)
that run on that page.

Normally you only get targeted instrumentation, but this will run the profiling
on the entire trace, so you can come look at the profile and see exactly what's
going on.  They also provide you with histograms of those 100 requests, so you
can see exactly what percentage of those requests fell within a secific range.




