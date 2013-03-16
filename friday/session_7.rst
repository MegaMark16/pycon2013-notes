Transforming Code into Beautiful, Idiomatic Python
===========================================================

**Presenter:** Raymond Hettinger

**Track:** VI

**Description:**

Learn to take better advantage of Python's best features and improve existing
code through a series of code transformations, "When you see this, do that
instead."

    https://us.pycon.org/2013/schedule/presentation/126/

Examples::

    for x in range(len(colors)):
        print colors[x]

    # Should be
    for x in colors:
        print colors


    n = min(len(names), len(colors))
    for i in range(n):
        print names[i], '-->', colors[i]

    # Should be
    for name, color in zip(names, colors):
        print name, '-->', color

    # But zip is slow, so you should use izip:
    for name, color in izip(names, colors):
        print name, '-->', color

Awesome components:

* zip/izip
* defaultdict
* Chain
* deque
* localcontext
* with open() as f:
* with ignored(SpecificException): do something that could throw an exception


