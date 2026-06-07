+++
title= "Introducing BoredFind: Browsing the Modern Web from a Scratch-Built OS"
date= 2026-03-03T22:48:46+01:00
draft= false
tags=[
  "boredos",
  "development",
  "networking",
  "osdev"
]
+++

If you've been following my work on **boredOS**, you know that I've been building the operating system entirely from scratch. Recently, that journey led me down the rabbit hole of creating my own custom network stack and even a bespoke web browser. 

But once you have a scratch-built browser, you quickly run into a massive problem: the modern internet is incredibly heavily bloated. Loading today's JavaScript-heavy websites on a minimalist, homebrew browser is a nightmare, but I still really wanted an easy way to actually surf the web from within my own OS.

Enter **BoredFind**.

## What is [BoredFind](http://find.boreddev.nl)?

BoredFind is a ridiculously lightweight search engine and web proxy. Under the hood, it hooks into DuckDuckGo to grab search results, but before it sends any website back to the browser, it aggressively strips the page down to the absolute bare minimum. 

It rips out the styling, scripts, and heavy DOM elements, converting complex websites into simple text and HTML 2.0-style hyperlinks. It even aggregates news from RSS feeds! Everything is constrained and normalized so that it renders perfectly and beautifully within my OS's VGA font limitations.

Boredfind also includes some RSS news feed functionality allowing you to read the latest news from various sources, including the BBC, NOS and the NPR.

## Why Build It?

I actually didn't want to build this at first. My original plan was to point my browser at **FrogFind**, an awesome project created by [Action Retro](https://www.youtube.com/c/ActionRetro) (whose channel and work I absolutely love) designed to let vintage computers browse the modern internet. 

It sounded like the perfect fit for boredOS. Unfortunately, when I tried it, I found that FrogFind wasn't able to load any searches and I remember it having a lot of sites it couldn't parse before it completely broke.

Since I had already built my own OS, my own TCP/IP stack, and my own browser... I figured I might as well build my own proxy, too. 

I whipped up BoredFind in PHP. It acts as the perfect middleman, taking the chaos of the 2026 internet and digesting it into a hyper-simple format that my browser can easily parse and display. 

There is something so satisfying about doing a web search when you wrote the OS, the network stack, the browser, *and* the search proxy. It's the ultimate giga chad coding experience.

Check [boredFind](http://find.boreddev.nl) out for yourself!

Also have a look at the [BoredOS Project.](https://github.com/BoredOS/boredOS)
*This article is originally from https://blog.boreddev.nl*
