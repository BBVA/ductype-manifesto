---
title: "Introduction"
description: "Doks is a Hugo theme for building secure, fast, and SEO-ready documentation websites, which you can easily update and customize."
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

# About the UNIX shell tradition

## What we don't like

1. It requires a lot of trying and error (or knowledge) to know what commands
   can be piped to what other commands.
2. Using a human friendly (plain text) format for input/output is good for
   humans, but bad for other programs.
3. The interface to declare pipelines is not very expressive.  If you need
   other than a straight data flow, you need to fall back to named pipes,
   background processes, etc.
4. Arguments to command are a mess.  There is no clear standard and no typing
   at all, which makes very difficult to write programs that call other
   programs.
5. Some programs don't even obey the standard tradition and reject standard
   input/output type of workflow, recurring to path to files provided as
   arguments.  This is a nightmare scenario for composability.  Some of then
   even rely on seeking the file, which makes it even more difficult.
6. Lack of unifying criteria in programs forces you to obtain a specialised
   knowledge for every one of them.
7. Shell scripting by definition rely on external commands which interfaces
   change continuously breaking everything all the time.  This makes it
   impossible to port from machine to machine or from one moment in time to
   another reliably.
8. Head of line blocking by default.  Head-of-line (HoL) blocking occurs in a
   pipe if there is a single piece of data waiting to be written,
   and the data at the head of the pipe cannot move forward due to
   being processed more slowly, even if other lines behind this one could.                     
9. No dependency management.  At most some scripts try to detect if you have
   the command install and fail with a helpful message.
10. There is no way to inspect the progress of a pipeline without stop the
    execution and do some `pv` trickery.
11. Arcane control flow.  Shell script control flow inherits all the problems
    described above by using the `test` or `[` command to evaluate the values.
    Making it very extraneous and error prone to programmers used to other
    languages.
12. It requires some experience to know how to transform data using shell
    commands.  You have to master grep, sed, awk, tr, cut, ... All text based.
13. Having data-transformation tools and data-producing tools in the same
    namespace is difficult to graps for some people.
14. Error control is too poor.  You only have a big red stop button.  Error
    control should be configurable so you can define what happens when a
    pipeline component crash.
15. No internal observability tools.  If you need to know how the process is
    going you have to watch the whole machine using top or similar.
16. Not all programs do only one thing and one thing right.  Even those that
    claims to do it are a subset (or superset) of others.
17. `tldr pages` exists because of 16.  We need to do better.
18. Commands (text filters mostly) are really many pure functions glue together.
    You have to select the one you want by navigating a nightmarish set of
    arguments.
19. Testing? Anyone?

