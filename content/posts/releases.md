+++
date = '2026-06-12T20:37:37+02:00'
draft = false
title = 'We have stopped making releases.'
tags=[
  "boredos",
  "dev log",
  "osdev",
  "important"
]
+++
No, we're not stopping with development of BoredOS, that will of course continue. We are simply stopping making releases (eg 26.6.0).

Maintaining releases creates a lot of friction, and we often see situations like this:

> *user*: I downloaded BoredOS and it doesn't boot

> *dev*: What version?

> *user*: idk, 26.6 or something

> *dev*: Try the nightly build

> *user*: wow that works

This happens frequently enough that we've decided releases aren't worth maintaining.

BoredOS is a free, open-source project, and building it does require some familiarity with how it works. If you're new to it, the `docs/` folder is a great place to start. When reporting issues, specific details go a long way. Things like logs, steps to reproduce, and your build environment help us actually investigate. "It just crashes" doesn't give us much to work with. And issues that don't give any usable information will simply be closed and ignored.

This will **never** be a perfectly polished operating system, **and that's okay**.

Going forward, the official and only way to run BoredOS is by cloning the repo, keeping it up to date, and building it yourself.