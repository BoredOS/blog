+++
date = '2026-06-07T14:46:52+02:00'
draft = false
title = 'BoredOS: Three years of building an OS from scratch (And loving every minute of it)'
summary = "The story of how a bad tutorial turned into a three-year (and ongoing) obsession."
tags=[
  "boredos",
  "yap",
  "dev log",
  "osdev"
]
+++
My name is Christiaan, and somewhere in late 2023 I followed a terrible tutorial on how to boot with GRUB and print text to the screen. That was a mistake. A wonderful, consuming, life-ruining mistake.

I got hooked immediately. Not because the tutorial was good  (it wasn't), but because something clicked when I saw those first characters appear on a screen running code I had written, on a machine that didn't know it was supposed to do anything at all. I started poking at things I didn't understand. I made some genuinely awful decisions. I shipped jank I'm still slightly embarrassed about. And I couldn't stop.

Flash forward three years: BoredOS has grown from that boot stub into a real UNIX-like operating system, over 380,000 lines of code, 12 contributors, 3 maintainers, nearly 200 GitHub stars, and 24 forks. It's had more name changes than I care to admit.

## What it actually does

BoredOS is a GP (General Purpose) operating system, and was always intended as such. It boots on real hardware (of course), drops you into a TTY using [the Bored Shell (bsh)](https://github.com/boredos/bsh) It has support for PS/2 inputs, framebuffer/VGA video, pcspk audio, IDE, AHCI, Networking, etc etc. Point is, it's a lot. In BoredOS i'm working on getting the syscalls as minimal as possible and using the VFS as much as i can. This VFS is of course, very UNIX like: `/dev` for devices, `/proc` for processes etc. Bog standard. Some recent additions to the kernel are: shm (Shared memory) and PTY's (Pseudo terminals.)

## What i got wrong (and learned from)

No OS journey is perfect, of course. Neither was mine. For some godforsaken reason, a few years ago, i decided to write all applications as header files, literally just C header files and have them directly into the kernel.. Really, what was i even thinking. Luckily this is no longer the case. BoredOS since recent actually grabs the whole userland (custom libc, coreutils, netutils etc.) from other repo's and puts these inside of external/. Once i actually got my userspace working years ago, i was using syscalls for just about everything. Even to interface with specific devices.. This now luckily all goes through the VFS and the only syscall left for a device is for the pcspk.. That's still on my list.. So yeah, it's not perfect. And there's no reason for it to be.

## The people who made it real.
I didn't expect anyone else to care about this, though I made some TikToks here and there showing off my OS, just to see what would happen. And then, out of nowhere, contributors started showing up. I still remember the surprise of seeing that first PR from a stranger - Someone who had just *found* the project and actually wanted to help it grow. That made me genuinely happy in a way I didn't expect. First came [Lucas (Lluciocc)](https://github.com/Lluciocc), a French guy who made some amazing PRs and is now a maintainer. Then the contributors just kept pouring in. Now sitting at 12 contributors and 3 maintainers. Me, [Lluciocc](https://github.com/Lluciocc), and [Mellurboo](https://github.com/Mellurboo). I'm so grateful to all of these amazing people.

## Where it's going.

BoredOS started with goals that were, honestly, all over the place. That's still very true - and i've made peace with it. Passion projects don't need a roadmap. They simply need dedication and love.

If any of this sounds interesting, the repo is [Available on GitHub](https://github.com/BoredOS/BoredOS). Contributions are welcome, questions and suggestions even more so. (Especially if it's pointing out the jank i need to fix.)
