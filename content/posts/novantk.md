+++
date = '2026-06-13T20:50:53+02:00'
draft = false
title = 'Building a compositor for BoredOS'
+++
Hi there, I'm Chris, the founder of BoredOS, as some of you may know by now.
For the last few weeks i've been working on [Nova](https://github.com/boredos/nova) a Wayland-style compositor specifically made for the BoredOS project.

## History
Previously, BoredOS was using a kernelUI for some reason - priorities I guess? Point is: it was super unstable and slow. About a month ago we completely removed that old window manager, along with the 30 million slow syscalls and apps made for it.

## Current
After removing all of that and basically starting over with the graphics for BoredOS, I started by replacing it with 10 TTYs — hardcoded to run bsh, which isn't amazing but good enough — and implementing Linux-like KD_GRAPHICS so apps like the Nova Compositor can take over a TTY to render everything. Instead of doing a whole mess for inputs, all inputs to userspace programs are simply handled by a `/dev/keyboardX` and `/dev/mouseX` device.

The compositor isn't all that *great* but it works.
 "nova is slow because however its interfacing with the fb is entirely fucked" - [Myles](https://github.com/mellurboo). SO i asked Myles to fix it xD. He's still working on it - and I'm still working on NTK, which is a massive amount of work covering every button, text input, and grid combination imaginable.

 # Design
 I was first going for a mix of Windows and MacOS, but to be real it looked ugly asf:
![Old UI](images/posts/novantk/oldstinkyUI.jpg)
Then i saw SerenityOS and uhh... Took some *light* inspiration.
![fancy retro UI](images/posts/novantk/slightlyinspiredlol.jpg)
And yes, it looks outdated. But that's not a bad thing. I actually really like it. BoredOS probably won't be running much real modern software anyways and i really love the retro look. It's also easier to run cause the computer doesn't need to render transparency for each pixel, which is slow, especially on a FB.

I guess this might just be me coping for making this design (it is) and.. That's fine. Yup.

## The journey

Working on Nova has been really good for me. I decided to use UNIX sockets, they were already half-implemented in LwIP, which turned out to be a great choice." It works quite well, though i did have to patch some holes that were wrong in LwIP though.. (Or something was wrong in my code, i don't really know. Point is it works.) I also had to add support for shared memory in the kernel so apps could actually write to Nova, to then be written into the back buffer and then the fb. With my initial implementation being super unstable, of course. 

What i currently have locally works pretty well and is *okay enough* - still does require quite a bit of work, and when i do push it, a lot of people are probably going to point out 10 million bugs i don't know how to fix. I guess that's just a part of the game.

## Thanks!

Thanks for reading my yap, if you want to see the current progress, i suggest checking out [the Nova repository](https://github.com/boredos/nova) for any commits coming out, and trying the Nightly build of BoredOS every now and often. Enjoy your day/night!

-Chris