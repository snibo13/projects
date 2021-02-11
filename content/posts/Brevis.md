---
title: "Brevis"
date: 2021-02-10T22:46:34-05:00
tags: ["Sophomore Year", "Mechanical Keyboards", "Electronics"]
draft: false
---

![Finished Macro Keyboard](../imgs/BrevisFull.jpg)

I spend a considerable amount of time on my computer, whether that is healthy or not is another issue but one thing that I've noticed is after working on writing or working on code my wrists will start to hurt. Combine this with a friend of mine getting Carpal Tunnel and the glory that is mechanical keyboards and you have me new interest in custom mechanical keyboards.

Ultimately the goal is to build a custom mechanical keyboard with a more ergonomic layout and maybe some custom keybinds. To that end I built a 7 key macropad with a rotary encoder.

![Schematic](../BrevisSchematic.jpg) ![PCB in KiCad](../BrevisPCB.jpg)

The first step in the process was understanding how mechanical keyboards work. Fundamentally, they are just matrices of switches where a row and column correspond to a specific key. The microcontroller, in my case an arduino pro micro, reads this in and sends the corresponding keycode to the computer. Alternatively, using a software suite called QMK you can program alternative actions besdes keypresses. 

![PCB Back](../imgs/BrevisFront.jpg) ![PCB Back](../BrevisBack.jpg)

Armed with the operating principles of a keyboard, I designed Brevis V1.0 the circuit that formed the circuit board you see below. I sourced some Gateron Brown Switches, order the PCB and soldered it up. This is the final result.

![Brevis Complete](../imgs/Brevis2.jpg)
![Rotary Encoder](../imgs/BrevisEncoder.jpg)


