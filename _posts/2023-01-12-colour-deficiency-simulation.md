---
layout: post
title:  "Simulating common colour vision deficiencies"
date:   2023-01-12 12:19:15 +0200
categories: image-manipulation bash
---

# Simulating common colour vision deficiencies

## Why should you care?
While most people can differentiate colours well, there is a surprisingly large portion of the population that consists of people with impairments regarding the differentiation of colours [Wikipedia](https://en.wikipedia.org/wiki/Color_blindness). Often this is referred to as colour blindness; however, most people with these conditons are not achromatic and do see different colours. The most prevalent type of colour vision deficiency affects up to 6% of the male population (colour vision deficiencies are much less prevalent in females). Therefore, if your figures are being viewed by a few hundred people, the chances are high that there is a part of your audience that has trouble differentiating colours. 
 
{% include image.html url="images/colour-deficiency-simulation/colourdef_red_green.png" description="This is how you see the image (most people see a strong colour contrast)" %}


## What can we do about it?
Not using colours at all would be a waste of opportunities. One would throw a powerful toolset over board, that could have been used to communicate ones findings in a more intuitive way than in grayscale figures. Thankfully, colour vision deficiencies can be simulated in order to understand what colour combinations are most problematic and which colour combinations are fine fro most people.


{% include image.html url="images/colour-deficiency-simulation/colourdef_red_green_deut.png" description="This is approximately how a person with deuteranopia sees the image, the fine hairlines are an artifact of exporting the image from a vector graphics program" %}


## Technical solutions
There is a variety of programs available to simulate the most common forms of colour vision impairment. Here are some of the solutions that I tried and and which worked out for me. Note that this selection is biased towards software that is free and available to use in Linux.

- [Color Oracle](https://colororacle.org/): This is a Java based application available for Linux, MacOS and Windows. Note that for this you need a suitable Java runtime environment and a system tray. The software creates a still view of the entire screen that disappears with the next mouse click or keyboard button push.

- [Daltonize python library](https://github.com/joergdietrich/daltonize): This is a python library that allows to convert image files. It can be used to integrate colour deficiency checking into your workflow by writing a shell script and executing it with a keyboard shortcut. No desktop environment is necessary for this. Here is how I use it on my laptop that currently runs the Qtile window manager.

```bash
#!/bin/bash
# This is based on the free and open programs scrot (screencapture), daltonize (deuteranopia filter) and feh (imageviewer)
# https://github.com/joergdietrich/daltonize
# Daltonize must not be used commercialy!

scrot ~/Pictures/deuter.png -o -q 100
daltonize ~/Pictures/deuter.png ~/Pictures/deuter.png -s 
feh ~/Pictures/deuter.png -F
```   

- [Custom Hot Corners - Extended (Gnome extension)](https://github.com/G-dH/custom-hot-corners-extended): This is an extension for the Gnome desktop environment that allows you to render a window with converted colours, so that you can actually work as if you were impaired. This allows you to tweak the colours without having to go back and forth as often as you would have to with the other two solutions presented above. If Gnome is your desktop environmaent of choice, this is probably the best solution out there. The extension serves as a frontend for the Gnome Universal Access tools and different functions can be grouped into custom menus, which then can be launched with keyboard shortcuts. 


{% include image.html url="images/colour-deficiency-simulation/gnome_ext_menu.png" description="This menu is accessible through the "extensions" app" %}

{% include image.html url="images/colour-deficiency-simulation/gnome_inkscape_deut.png" description="The custom menu after being launched with a keyboard shortcut" %}


