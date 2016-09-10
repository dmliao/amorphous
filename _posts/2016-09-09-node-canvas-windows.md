---
layout: post
title: Notes on Installing Node Canvas for Windows
wip: true
---

I develop on Windows. I do this for a variety of reasons, primarily because my personal laptop uses Windows, because I run a variety of software that only runs on Windows, etc. etc. etc.

Unfortunately, a _lot_ of open source software does not build on Windows, or have rather complex build processes that involve installing several versions of Visual Studio or other interesting schenanigans. Or the install process uses shell scripts, which Windows doesn't quite work with yet. (Windows 10 is going to have bash built in at some point, or so I hear...but I'm here on Windows 8 still.)

So, here I am trying to finagle my setup into being able to install libraries from Github that might not have the best Windows building instructions. Or at least, finding alternatives that do similar things to what I'm used to on Linux or OSX.

The latest headache on that end? Getting `node-canvas` to work. `node-canvas` is a native library (in C or C++, I believe?) and so needs to be built with system-specific compilers...which Windows has a hard time with. In fact, the README page for the `node-canvas` project has one-liner shell scripts for building on Linux and OSX, and an [entire wiki page for Windows](https://github.com/Automattic/node-canvas/wiki/Installation---Windows).

Not that I was able to build it just by following the wiki, for that matter. Here are just a few notes on the steps I had to take to get it working on my system:


https://github.com/Automattic/node-canvas/issues/619#issuecomment-229696497
