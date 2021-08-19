---
title: "Brevis"
date: 2021-02-10T22:46:34-05:00
# tags: ["Sophomore Year", "Mechanical Keyboards", "Electronics"]
summary: " A 7-Key macropad with rotary encoder designed from scratch"
draft: false
---

![Finished Macro Keyboard](../imgs/BrevisFull.jpg "The Finished Macro Board")

I spend a considerable amount of time on my computer, whether that is healthy or not is another issue but one thing that I've noticed is after working on writing or working on code my wrists will start to hurt. Combine this with a friend of mine getting Carpal Tunnel and the glory that is mechanical keyboards and you have me new interest in custom mechanical keyboards.

Ultimately the goal is to build a custom mechanical keyboard with a more ergonomic layout and maybe some custom keybinds. To that end I built a 7 key macropad with a rotary encoder to get some experience with circuit dsign and the specifics of keyboard design.

![PCB in KiCad](../imgs/BrevisPCB.jpg "PCB designed in KiCad")

The first step in the process was understanding how mechanical keyboards work. Fundamentally, they are just matrices of switches where a row and column correspond to a specific key. The microcontroller, in my case an Arduino pro micro, sends columns high and reads in the rows sequentially. It then translates these readings to keycodes and sends them to the computer. The software I used to program the computer, called QMK, also allowed a single switch to map to multiple keypresses or other actions.

![PCB Front](../imgs/BrevisFront.jpg "Manufactured PCB")

Armed with the operating principles of a keyboard, I designed Brevis V1.0 the circuit that formed the circuit board you see below. I sourced some Gateron Brown Switches, order the PCB and soldered it up. There was one small problem, the right most column of the keypad would not worked. I double and triple checked the schematic and it all seemed like it should be connected. I hooked up a multimeter and the keys in the column were reading the same voltage as all the other keys. Thanks to some research and a helpful Redittor I found the culprit. The schematic as originally designed had the last column pass through two diodes in series. While my electrical engineering lectures did cover voltage drops across resistors, I had never considered that diodes would have a similar drop, the second column was fine because the drop across the diode was not large enough for the arduino to read the value as low. I refactored the design so that the keys each only passed through one diode and it works like a charm now.

<!-- ![Brevis Complete](../imgs/Brevis2.jpeg) -->


