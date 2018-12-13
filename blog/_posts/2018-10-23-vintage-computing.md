---
title: 'Vintage Computing'
layout: post
tag: [computing]
date: 2018-10-23 23:00:00 +0800
---

Last week, I learnt about [Micro Mages](http://morphcat.de/micromages/), a new game for the NES from [Morphcat Studios](http://morphcat.de/). The game looks great, sounds great, and _fits into 40KB_. [This video](https://youtu.be/ZWQ0591PAxM) clearly explains the ideas behind the code and graphics optimisation.

<!--more-->

For those from a different generation, the [Nintendo Entertainment System](https://en.wikipedia.org/wiki/Nintendo_Entertainment_System) was a 8-bit video game console that dominated the market in the 80s, in the days before such modern luxuries as GPUs, sound cards, and digital monitors. The hardware specs leads one to wonder how it was possible to do _anything_ on the NES:
- an 8-bit CPU at 1.79MHz, with 2KB RAM;
- a Picture Processing Unit with a palette of 54 colours, that draws a background and (up to 64) $8\times8$ sprites onto a $256\times240$ screen;
- an Audio Processing Unit with five channels (two square wave, triangle wave, noise, and digital samples);
- ROM is stored on the game cartridges, ranging from 40KB (like in Micro Mages, or the original Super Mario Bros.) to 1MB in extreme cases.

With these restrictions, even programming in C was a luxury that game developers could not afford. Everything had to be done in [assembly code](https://en.wikipedia.org/wiki/Assembly_language), which gave fine control over the program in order to save on precious bytes:
- combining $8\times8$ tiles into fixed patterns of $16\times16$ meta-tiles (or even $32\times32$ meta-meta-tiles), so that only a pointer to a dictionary needs to be stored instead of the entire pattern;
- custom data structures to store object data, enemy AI, etc.;
- compression algorithms (such as run-length encoding) to efficiently store level and music data;
- and so on.

The bit-level hacking and trickery used by programmers at the time, and hobbyists for vintage hardware today, is just astounding. Here is a random list of my favourites:
- The [fast inverse square root algorithm](https://en.wikipedia.org/wiki/Fast_inverse_square_root) is a classic, computing the function $\frac1{\sqrt x}$ by hacking the _actual hardware representation_ of a floating-point number!
- [Bass kicks in NES music](https://youtu.be/Jd6nyynuzio) can be simulated by quick downward pitch bends on the triangle wave audio channel.
- Some people have even achieved [_1024 colour_ display](https://int10h.org/blog/2015/04/cga-in-1024-colors-new-mode-illustrated/) on an unmodified IBM PC (1981), which should only be able to show 4 colours at a time!

I'll conclude this post with a list of different implementations of the music video for the song [Bad Apple!!](https://youtu.be/FtutLA63Cp8) on vintage platforms. The differences across these versions give a sense of the limitations of these platforms, and the kinds of hoops that one has to jump through to get the animation working. 
- [Bad Apple!! on NES](https://youtu.be/qRdGhHEoj3o)
- [Bad Apple!! on Atari 2600](https://youtu.be/FtutLA63Cp8)
- [Bad Apple!! on Sega Genesis](https://youtu.be/2vPe452cegU)
- [Bad Apple!! on the IBM PC](https://youtu.be/MWdG413nNkI?t=172); notice how the animation occasionally takes several frames to update, so [the video codec](https://trixter.oldskool.org/2014/06/19/8088-domination-post-mortem-part-1/) must be more sophisticated than a frame-by-frame image dump.

Keep in mind that these are original hardware from the 1980s, rendering full-resolution video. Imagine walking into a computer store 35 years ago and seeing _that_! This makes me wonder: with our massively improved hardware capabilities today, how much of the true power of computation remains untapped and unexplored?...