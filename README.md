# Applied Functional Programming Course

[![Build Status](https://travis-ci.org/qfpl/applied-fp-course.svg?branch=master)](https://travis-ci.org/qfpl/applied-fp-course)

<img src="https://i.imgur.com/0h9dFhl.png" height="400" width="640" />

This is a brand new course, so there are going to be rough edges. We invite you to submit issues or
pull requests if you find errors or have suggestions on how to improve it.

This course is designed to be run in a class room with instructors, but we would like to make it
suitable for self-study as well. Although undertaking this course outside of the workshops will
increase the difficulty somewhat, we do not discourage it and invite suggestions on how to make the
course more approachable.

If you do attempt this on your own and find yourself completely lost, then you may come find us on
IRC on [Freenode](https://freenode.net/) in #qfpl or #fp-course.

### You:

* Have completed, or are capable of completing, the [Data61 FP Course](https://github.com/data61/fp-course).
* Have a few months self-study to your name.
* Want to know how to build larger applications with statically typed FP.
* Are willing to accept that a web application is a sufficient choice.
* Can write the canonical function of type: ``Applicative f => [f a] -> f [a]``

### We:

* Have constructed a sequence of goals of increasing difficulty.
* Have provided a framework within which to apply these goals.
* Have included relevant components of larger applications:
  * Package dependencies
  * Project configuration
  * Application testing & building
  * Encoding / Decoding messages (JSON & Binary)
  * Persistent storage integration
  * App state & configuration management
  * Error handling & reporting
* Will utilise both type & test driven development techniques.
* Will explain architectural and design trade-offs when appropriate.

### Setup build tools:

Each level is a self-contained Haskell module, containing incomplete, or as yet
undefined, data types and functions.

We recommend using either a cabal sandbox, or a ``nix-shell``, depending on your
preference.

To use a sandbox:

```bash
$ cd path/to/applied-fp-course
$ cabal sandbox init
$ cabal install --only-dependencies --enable-tests
$ cabal build
$ $EDITOR README.md
```

We do recommend using cabal sandboxes as they provide a contained Haskell
environment for a given project. Easy to clean up, and package versions won't
conflict with any other sandboxed project you may be working on.

If you're using a version of Cabal that is >=2.0 (use ``cabal --version`` to
find out), then you can use the ``new-*`` commands and you don't need a sandbox:

```bash
$ cd path/to/applied-fp-course
$ cabal new-configure --enable-tests
$ cabal new-build <levelN>-exe
$ $EDITOR src/<LevelN>/README.md
```

The normal cabal build commands should then work as expected.

To use the Nix Shell:
```bash
$ cd path/to/applied-fp-course
$ nix-shell
$ cabal new-build <levelN>-exe
$ $EDITOR src/<LevelN>/README.md

```
Once that completes you will be in a ``nix-shell`` environment with all the
tools required to build the application for that level. Note that the
levels build on each other, so you can go to the highest level and enter a
nix-shell there, you will then have all the required tools for every level.

The ``shell.nix`` is not provided, so if you have a different work-flow you can
utilise the derivation from the ``applied-fp-course.nix``.

##### Stack

Stack yaml configuration is provided and checked by our CI system for successful
builds. However the authors do not use stack, so we cannot promise to be able to
resolve stack related issues that may arise. Though we will do our best. :)

##### Please note...

These lessons are designed to be completed with an instructor as part of the
Data61 Applied Functional Programming Course. You are of course welcome to
clone the repository and give it a try, but you may find the tasks more
difficult. If you have any questions we can be contacted in the
Freenode [#qfpl or #fp-course IRC channel](https://freenode.net). You can use the
free [WebChat client](https://webchat.freenode.net).

#### Subsequent lessons may contain spoilers, don't cheat yourself out of the experience!

There is a ``README.md`` file in each Level module folder that will provide
instructions about what the goal is for that specific level.

* Level 01 : Simple Hello World web app.
* Level 02 : Define our application spec with types!
* Level 03 : Testing & Tools (hspec & ghcid)
* Level 04 : Database layer (sqlite-simple)
* Level 05 : Add some flexible configuration
* Level 06 : ReaderT & Refactoring
* Level 07 : ExceptT & Refactoring

-- Coming Soon...
* Level 08 : (Bonus Round) Lenses & Refactoring

-- Maybe...
* Level 09 : Add session controls (login, logout) and a protected route. So we
  can have something that resembles application state. For the purposes of
  modelling the state machine and implementing some property based tests.
