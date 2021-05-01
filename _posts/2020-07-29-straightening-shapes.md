---
layout: post
title:  "How to straighten curved shapes using Inkscape"
date: "29.07.2020"
category: vector-graphics
---

# Step 1
Draw the outline using the Bezier tool. Then draw the midline according to what you see in the base image.

{% include image.html url="images/straightening-shapes/straightening_1.png" description="Outline and midline drawing on the base image. Base image:  *Elthusaacutinasa* sp. from Van der Wal et al. 2019 *ZooKeys*" %}

# Step 2
Then rotate the outline and the midline, so that the midline is horuzontal (the ends of the midline should be at the same level).

{% include image.html url="images/straightening-shapes/straightening_3.png" description="Rotated shape and midline" %}

# Step 3
Vertically mirror the midline (by pressing "v") and move the mirrored midline up or down so that the lines are tangents of each other.

{% include image.html url="images/straightening-shapes/straightening_3.png" description="Mirrored and correctly placed midline" %}

# Step 4
Then select the Bezier tool and adjust its mode to be "Bend from clipboard". With the bezier tool try to redraw the mirrored midline as precisely as possible. For the end points to correctly align, the snapping behaviour of Inkscape can be used. Another shape should appear by releasing the Bezier tool with a right click.

{% include image.html url="images/straightening-shapes/straightening_4.png" description="Straightened shape on top of the previously drawn objects" %}

# Step 5
Remove everything but the new shape.

{% include image.html url="images/straightening-shapes/straightening_5.png" description="Straightened shape" %}

# Step 6

Do not forget to **set the mode of the Bezier tool back to "none"** when you are done. Otherwise you will regret it later.