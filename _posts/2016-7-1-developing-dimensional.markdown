---
layout: post
title:  Developing Dimensional
summary: Some tips and tricks towards idiomatic Python while developing Dimensional.
date:   2016-7-1-10:23:00
categories: development data
---
I love holiday weekends.  For me, I tend to work on some coding project around a barbecue or big meal of some kind.  This weekend it's all about [dimensional](#) and putting some distance between me and start.

The trick has been to embrace idiomatic Python practices.  I usually use Python as a utility language.  I'll do some basic work on data, almost always in a Jupyter notebook.  It's really powerful, used that way.  Building a package is something different.

## Manual Tests

I like to test drive my code.  Manual tests count.

If I do this, what happens next?  Right?

Exactly.  Just do something and understand it.  Interact with the code and keep making small changes.

How do you do this?

I started with iPython.  That worked fairly well.  I had issues with reload! not working consistently.

Seems like there was a warning that there is no guarantee of consistency with reload!

Yeah, not a very comforting bit of news.  I ended up just exiting iPython a lot and restarting.

Wasn't that a pain?

Well, I started writing functions to get back to the same starting point.  This is why automated tests are a great thing.  But, I was dealing with things that could go in any direction.  I just needed to get something better than iPython for manual tests.

What did you do?

Go back to me sweet spot, Jupyter.  But not without a few problems.  Getting the code to run in a Jupyter notebook was a little tricky.  I ended up with this:

    %load_ext autoreload
    %autoreload 2

    import os
    os.sys.path.append(os.path.dirname(os.path.abspath('..')))
    import dimensional as dim

What does this do?

[Autoreload](https://ipython.org/ipython-doc/3/config/extensions/autoreload.html) watches for file changes.  It doesn't remove functions from the namespace when I remove them in my code, but it keeps up nicely with my changes.

Nice, and the path stuff?

I explicitly set the path to my source root.  (I found notes on this [here]((http://stackoverflow.com/questions/11536764/attempted-relative-import-in-non-package-even-with-init-py))).

Source root?

Yeah, this was something different for a Python package, versus a lot of other development environments.  A lot of other build environments expect a lib, src, or app to put the main source code.  Configuration, tests, documentation, and other things stay out of the source root.  Python likes to name this after the package.

Why is this?

I think it has to do with their module philosophy.  We stick `__init__.py` in a directory, and it becomes a module.  We want the naming of that to be less surprising to our developers.  Whatever the reason, I needed Jupyter to be able to load all my code, so I add those lines.  Finally, I just import dimensional directly.

This seems like a lot of work.  Why did you do this?

Well, automated tests are better once I am pointed in a clear direction.  All the setup is done once.  All the environments can run them.

## Automated Tests

I noticed there are a lot of ways to do this in Python.  How did you set up?

Well, I looked at [nose2](https://github.com/nose-devs/nose2) and decided that I didn't want to go add anything special until I had a reason for it.  I stuck with [`unittest`](https://docs.python.org/3.5/library/unittest.html) and `MagicMock` from `unittest.mock`.  I use the recursive test discovery tools that ship with Python.  I added the following Makefile to my code:

    init:
      pip install -r requirements.txt

    test:
      clear
      python -m unittest discover -s tests -v

What does this do?

Well, for the test part, `python -m unittest discover` uses the built-in test discovery.  I ask it to start in my tests directory and return verbose test results.  I also add a few magic lines at the bottom of every test file:

    if __name__ == '__main__':
      suite = unittest.TestLoader().loadTestsFromTestCase(TestDimensional)
      unittest.TextTestRunner(verbosity=2).run(suite)

The `__name__ == '__main__'` is idiomatic Python.  It checks if the file is being run directly, rather than being imported from another location.  If I try and run a single test file, it will load the test suite from the file and run it.

So, you just run `make test` or `python path/to/test_file.py` to run tests?

That, and I also have my favorite way of running tests while I work:

    find ./dimensional/entities  | entr -c make test

This says that any time I change a file in dimensional/entities, all my tests should run.  If that gets too confusing, I can run

    `find ./dimensional/entities | entr -c python tests/entities/test_entities.py`

and just run a few tests.

# FIXME: get this to actually work with a dependence on dim

What is `entr`?

The entr package is not commonly installed on developer machines, but it's small and is a quick tool for reacting to changes in a stream.  Here, I ask it to clear the screen with `-c` and then run my tests as my Makefile understands them.

Any surprises with automated tests?

One thing that was surprising was that I need `__init__.py` in any subdirectory for the test runner to recursively discover all of the tests.

Surprising?  Isn't this the Python way?

Yes, but not second nature to me.  Now I remember.

## Unittest Specifics

What about the actual tests?

There was this exercises I did as I read through the unittest documentation.  Basically, I wanted all of the tools I'd most-likely want and make sure I understood them:

    import unittest
    from unittest.mock import MagicMock

    class Bar(object):

      def thud(self):
        return "thunk"

      def baz(self):
        return self.thud()

    class TestDimensional(unittest.TestCase):

      def setUp(self):
        self.subject = "foo"

      @unittest.skip("using skip")
      def test_true(self):
        self.assertTrue(True)

      @unittest.expectedFailure
      def test_weird(self):
        self.assertTrue(False)

      def test_foo(self):
        self.assertTrue(True)
        self.assertEqual("foo", self.subject)

      def test_bar(self):
        thing = Bar()
        thing.thud = MagicMock(return_value="foo")
        result = thing.baz()
        self.assertEqual("foo", thing.baz())

      def tearDown(self):
        self.subject = None
        # Just for example, no reason to tear down I should think (in this case)

    if __name__ == '__main__':
      suite = unittest.TestLoader().loadTestsFromTestCase(TestDimensional)
      unittest.TextTestRunner(verbosity=2).run(suite)

OK, you're going to have to walk me through this one.

My generic setup needs a few tools:

    import unittest
    from unittest.mock import MagicMock

That gives me `unittest` and `MagicMock`.  Skipping the temporary Bar class, I have a regular test suite.  It inherits from `unittest.TestCase`.  Inside there I have `setUp` and `tearDown` that work about as all unit test suites work.  My actual tests are defined with `def test_`, much as other unit test suites as well.  The directives that I thought I might use are `@unittest.skip` and `@unittest.expectedFailure`.  `thing.thud = MagicMock(return_value="foo")` is my example of setting up a mock.  The test loader stuff I already explained.

That's an ear full.

Sorry, I wanted to leave notes so that someone would have a shortcut, but the [unittest documentation](https://docs.python.org/3.5/library/unittest.html) is really sufficient.

## Directory Structure

I found [The Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/) to be the most informative descriptions for many of my tasks.  Specifically, I liked their [Structuring Your Project](http://docs.python-guide.org/en/latest/writing/structure/) article.  My top-level structure currently looks like this:

    .
    ├── LICENSE
    ├── Makefile
    ├── README.rst
    ├── TODO.rst
    ├── data
    ├── dimensional
    │   ├── __init__.py
    │   ├── entities
    │   ├── interfaces
    │   ├── manual_tests
    │   └── service_objects
    ├── docs
    │   └── use_cases
    ├── requirements.txt
    ├── setup.cfg
    ├── setup.py
    ├── tests
    │   ├── test_dimensional.py
    └── tmp

I omitted a lot of the details so I could point out the basic setup.  Most of it comes from the Guide.

I organized my package code somewhat after [Uncle Bob Martin's Architecture ideas](https://blog.8thlight.com/uncle-bob/2012/08/13/the-clean-architecture.html).  For dimensional in particular, I need to keep upstream and downstream implementations free of our code.  So databases, data sources, libraries needed for sources and uses of our data all get to be strictly left out of code.  I need to keep the CLI separate, as well as any UI interface we may choose to build.

I keep use cases inside my docs directory.  For me, having a folder full of hand written notes, a series of uses cases, good chat tools around a project all contribute to the dialog parts of writing software.  The conversation drives the thought process and having some of that explicit near my project brings it up to speed faster.

I also leave a TODO file in there for myself.  I instruct git to ignore that, so it's not getting messy for other people.  We use Github's Issue Tracker for collaborative issues that need attention.  This just keeps notes handy where I need them.

# FIXME: Make sure this still works well with more tests, more code, and more documentation

## Git Ignore

Leaving things out of the repository can be important.  Here is my current .gitignore file:

    # Allow local todo lists
    TODO.rst

    # Ignore pycache
    __pycache__

    # Ignore local test data
    data

    # Ignore any generated code
    *.pyc

    # Ignore Environment configuration
    .env

I want to leave a place to have local data, local todo lists, local cache and local byte code.  Also, if my local use of the package integrates with any other system, I put the configuration for that in my .env.  That way passwords, API tokens, and similar bits of code never leave my laptop.

## Laziness

One thing I want for dimensional is a way to make the code evaluate lazily.

What does that mean?

That means I want to completely specify the whole data chain and then be able to use that as an object without actually having to process the code.

Why?

If I have a lot of data, I can look at the description of the data without slowing down.  Even if I don't have a lot of data, I want to have my organization before I realize the data.

OK, what did you learn about this?

I got stuck on it, frankly.

for row in collection...
## Documentation

## Python Functions

## Doc Strings

A lot of people don't like using inline comments for more than minimal clarification.  The Python community has embraced verbose commenting with vigor, so I embrace this with them.  It's better to have a productive next-in-line developer than it is to be right (or smugly think I'm right).

## Classes vs Modules

## Functional Programming

In order to embrace a separation between business logic and external dependencies, I pass an actor around to my functions a lot.  E.g., if blaze or petl can fulfill a task for me, I pass in a reference to that code and then send it the data it needs to do its job.  That way, when the next hot thing arrives, I can send code to that as well.

This means I can embrace the [`functools`](https://docs.python.org/3.5/library/functools.html) a little.

* give
* some
* examples

## Attributes

## CLI

We decided to use X for our command line interface.  It has all the tools that we needed.  I broke the interface into a tree of applications, so no single part of the CLI was too complicated to use.  Here is an example of that:

    FIXME: Add samples

Since I built the main package before I wrote the CLI, I already had a strong set of use cases complete and accessible to the CLI.  Making dimensional actually useful for someone extended those use cases as well.  It was a nice dance between the inside-out thinking that architects a larger package and the outside-in thinking that makes that package useful to real people.

## Configuration

Python likes to use [`configparser`](https://docs.python.org/2/library/configparser.html) and .cfg format for configuration.  So, we embrace that.  It looks like this:

    Update the config example

We also embrace a tree of possible configuration.  So, we take a default set of configuration settings, look in the home directory and the local directory for configuration we can add in.

## Python 2.7 vs 3.x

A lot of data people use Python 2.7.  FIXME: Add the reference here.  How do you handle the differences?

Unfortunately, Python seems stuck in the past.  A lot of good features are added to Python 3, a lot of good libraries are not compatible.  I decided to target Python 3.5 and retrofit older versions of Python.  There are a lot of good tools like the `__future__` module that make that easier.