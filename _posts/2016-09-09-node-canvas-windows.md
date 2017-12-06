---
layout: post
title: Node Canvas on Windows 8
---

I develop on Windows. I do this for a variety of reasons, primarily because my personal laptop uses Windows, because I run a variety of software that only runs on Windows, etc. etc. etc.

Unfortunately, a _lot_ of open source software does not build on Windows, or have rather complex build processes that involve installing several versions of Visual Studio or other interesting schenanigans. Or the install process uses shell scripts, which Windows doesn't quite work with yet. (Windows 10 is going to have bash built in at some point, or so I hear...but I'm here on Windows 8 still.)

The latest headache on that end? Getting `node-canvas` to work. `node-canvas` is a native library (in C or C++, I believe?) and so needs to be built with system-specific compilers...which Windows has a hard time with. In fact, the README page for the `node-canvas` project has one-liner shell scripts for building on Linux and OSX, and an [entire wiki page for Windows](https://github.com/Automattic/node-canvas/wiki/Installation---Windows).

Not that I was able to build it just by following the wiki, for that matter. It took a bit to figure out that there was something wrong with `node-gyp`, which was solved by going in and manually [editing a file in my global `node-gyp` install, according to these instructions](https://github.com/Automattic/node-canvas/issues/619#issuecomment-229696497).

Apparently this behavior was due to some changes in 2015+ versions of the Visual Studio compiler, and has since been fixed. But if there are issues with the `win_delay_load_hook.` file when installing `node-canvas` (or possibly other `node-gyp` dependent modules), this might be to blame. It certainly took me way too much time to figure it out.


