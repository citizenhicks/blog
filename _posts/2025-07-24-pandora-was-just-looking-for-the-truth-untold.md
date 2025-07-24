---
layout: post
title: "pandora was just looking for the truth untold"
date: 2025-07-24
author: "citizenhicks"
tags: ["colemak-dh", "tmux", "neovim", "kitty", "split keyboard"]
---

pandora’s search for the truth untold represents our relentless pursuit of knowledge, even when it risks chaos or destruction. this is exactly what happened when I decided to change my integrated development environment and QWERTY keyboard layout to terminal-based development and Colemak-DH layout on a split keyboard. this post will deep dive into the workflow I currently use to experiment with language models, reinforcement learning algorithms, and to build multi-agent systems for production.

## the keyboard journey

the last 17 years before I transitioned to a split keyboard and Colemak-DH, I typed QWERTY on a normal keyboard with 8 fingers at best. how I usually approach change is the most painful way possible: everything all at once. the transition to a split keyboard was no different. to add a bit of context, my typing speed in English on monkeytype.com was around 90 words per minute (WPM), with relatively low accuracy of 90%. 4 months into the Colemak journey, now I type 100 WPM with 98% accuracy, with the added benefit of typing longer and more comfortably due to the split keyboard setup. this is mainly due to the fact that now I properly touch type, and the key switches I use, which are linear 35g silent switches, keep the typing fast and effortless with proper layering and home row mods as it should be.
having Colemak-DH as a main typing layout, however, gave a lot of challenges when it comes to the terminal setup. as you may know, tmux, Neovim, and terminal environments in general are based on the concept of keyboard-only engagement with your computer, and the keyboard shortcuts are set up for QWERTY layout.

## the terminal
### kitty
my daily driver is the Kitty terminal on both macOS and Linux systems. I tried many terminals, and Ghostty and Kitty were the front runners due to ease of configuration and responsiveness. I find Kitty’s text rendering a wee bit better (crisp text), and I find Kitty faster with tmux, Neovim, and fzf fuzzy finder, but I have not benchmarked these terminals against each other; it is more of a preference. I use JetBrains Mono Nerd Font and slight tweaks to the keyboard shortcuts. I have command + neui to move around in the terminal as opposed to arrow keys, as my keyboard layout has the arrow keys on the second layer, and I found that this is a faster way of navigating in Kitty. the drawback of this setup is that you get used to this key combination, and you need to carry your config around to other systems if you like to SSH into your servers from a different laptop.

### tmux
I started with just one terminal window, then later started to use Zellij, which is a Rust-based terminal multiplexer with a helpful keyboard shortcut hint bar. after a while, I realized that tmux has a massive community and a lot more very useful plugins, so I finally transitioned to tmux, and I do not regret this at all, even when I think back to the one full day of configuration and styling I spent on tmux on a nice sunny Sunday. in general, the setup of all these tools takes a wee bit longer than for the QWERTY-typing community, and you also need to think of the clashes of key combinations, which is somewhat present in tmux as well. my simplest and system-agnostic solution to this is layering of the split keyboard. instead of remapping critical and most-used keys, I just map them to a second layer. this is true for the leader key, how I split panes, and navigate between windows and sessions.
I also find it very effective to work with Yazi and fzf in tmux. I tried various file system plugins in tmux, but none of them really worked well, so I landed on the simplest solution, which is Yazi. fzf made it to my workflow in the last month or so, which is the result of me getting more comfortable with tmux and the philosophy of text-based engagement with your computer.

### neovim
my Neovim setup took the longest time to finish. it has countless plugins and a lot of customization when it comes to the status bar or the shortcuts. here are a couple of thoughts on certain parts of the setup:

- I think the most critical part to nail with Neovim is the debugging environment setup. from my VS Code days, that just felt so easy to do in an IDE, but somehow not that intuitive in Neovim. I have configured the system, changed many of the settings, and now I feel like the debugging experience and workflow is on par with an IDE such as VS Code.
- keyboard shortcuts had to change, but mostly induced by the remapping of 'hjkl' keys to 'neui' keys. if you are familiar with Neovim shortcuts, i, e, u, n all have frequently used functionality, so all this had to change. some were easy, such as h -> n, and n -> h mapping, given how these are placed on a Colemak-DH keyboard; it made sense. some are a bit trickier, such as i, which I remapped to y. as you may realize, y is yanking and frequently used. these are just prime examples of the Colemak-DH life with Neovim, and there are many such cases...
- the last part I want to highlight here is the text suggestions and linting. there are competing plugins for all of these tasks, and you need to find the option that works best for you. I like relatively non-intrusive linting messages with not too aggressive text suggestions, but that is just my preference. in Neovim, you can go crazy and get all the suggestions and messages you need.


## is it worth it?
well, looking back on this journey and how the coding models evolved in the last couple of months, I definitely prefer this way. part of it is the fact that Claude Code and similar tools live in the terminal and just make it much easier to work with in tmux. some part is the fact that I use a split keyboard, which will naturally make you use it a bit more, given the customization capabilities and layering of the keys. once you get used to not moving your hands at all, as everything is right where it should be on the home row, it’s hard to reach for your trackpad/mouse when you really have to. overall, I really enjoy the workflow as it is at the moment, but as any tmux-Neovim-split-keyboard-Colemak user will tell you, your config will never be done. thanks for reading.

_find me on [X/Twitter](https://x.com/citizenhicks) or [GitHub](https://github.com/citizenhicks) for more discussions about ai and software engineering._
