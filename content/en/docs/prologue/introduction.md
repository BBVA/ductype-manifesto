---
title: "About the UNIX shell tradition"
description: "This is a WIP document about the design of Ductype"
lead: "Doks is a Hugo theme for building secure, fast, and SEO-ready documentation websites, which you can easily update and customize."
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 100
toc: true
---

# What we don't like

## Organic growing produces a confusing structure

- It requires a lot of trying and error (or knowledge) to know what commands
  can be piped to what other commands.
- Some programs don't even obey the standard tradition and reject standard
  input/output type of workflow, recurring to path to files provided as
  arguments.  This is a nightmare scenario for composability.  Some of then
  even rely on seeking the file, which makes it even more difficult.
- Lack of unifying criteria in programs forces you to obtain a specialised
  knowledge for every one of them.
- It requires some experience to know how to transform data using shell
  commands.  You have to master grep, sed, awk, tr, cut, ... All text based.
- Having data-transformation tools and data-producing tools in the same
  namespace is difficult to graps for some people.
- Arguments to command are a mess.  There is no clear standard and no typing
  at all, which makes very difficult to write programs that call other
  programs.
- Not all programs do only one thing and one thing right.  Even those that
  claims to do it are a subset (or superset) of others.
- `tldr pages` exists because of "Not all programs do only one thing".  We need
  to do better.
- Commands (text filters mostly) are really many pure functions glue together.
  You have to select the one you want by navigating a nightmarish set of
  arguments.


## Command line program output is not mean to be consumed by computers

- Using a human friendly (plain text) format for input/output is good for
  humans, but bad for other programs.
- Limited to a text interface.


## There is just one way to compose programs and it doesn't solve all problems

- The interface to declare pipelines is not very expressive.  If you need
  other than a straight data flow, you need to fall back to named pipes,
  background processes, etc.
- Head of line blocking by default.  Head-of-line (HoL) blocking occurs in a
  pipe if there is a single piece of data waiting to be written,
  and the data at the head of the pipe cannot move forward due to
  being processed more slowly, even if other lines behind this one could.                     
- There is no way to inspect the progress of a pipeline without stop the
  execution and do some `pv` trickery.
- Error control is too poor.  You only have a big red stop button.  Error
  control should be configurable so you can define what happens when a
- No internal observability tools.  If you need to know how the process is
  going you have to watch the whole machine using top or similar.


## There is no composable way to bundle a script with all its dependencies to make it portable

- Shell scripting by definition rely on external commands which interfaces
  change continuously breaking everything all the time.  This makes it
  impossible to port from machine to machine or from one moment in time to
  another reliably.
- No dependency management.  At most some scripts try to detect if you have
  the command install and fail with a helpful message.


## Shell script development is painful

- Arcane control flow.  Shell script control flow inherits all the problems
  described above by using the `test` or `[` command to evaluate the values.
  Making it very extraneous and error prone to programmers used to other
  languages.
- Testing? Anyone?


# What we do like

1. Faster than writing a program.
2. Explorability is to the roof.  You can fail fast trying to solve a problem
   or data transformation and iterate towards the solution like in no other
   environment.  Other solutions like Jupyter Notebook and the like are trying
   to do the same.
3. The repl model forces you to adhere to a fire and forget model.  Making it
   easier to write code that is a pure data transformation by nature.
4. Pipes are the fastest way of high-level programming. Composability at its best.
5. There are only a few programs that don't expose a command line interface.
   You can interact with everything from security tools, to cloud providers, to
   super computers, etc.
6. If bash doesn't run you have a hardware problem.  Shells are not coupled to
   the programs they use.
7. Its obiquitous.
8. Using only the keyboard makes you fast by default.
9. The fastest feedback loop known to man.


# Things that are and there are no other way

1. A shell is like your best friend, drunk at 4am.  It will do whatever you
   want immediately, it's super agreable.  If you screw up with writting the
   command it will run it without questioning you.
2. When you write a command or a script you cannot ask what would be the plan
   before executing it.
