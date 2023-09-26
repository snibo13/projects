---
title: "Keyboard Update II - LVGL and Shift Registers"
date: 2023-07-06T14:45:37-07:00
draft: false
list: true
summary: "Second development log on the keyboard"
color: "#41BBD9"
---


There are three major differences between the keyboard I am working on now and the macropad I made a few years back. The first is the software. Rather than using QMK, an open-source keyboard development framework, I am writing all the firmware from scratch using the Pi Pico SDK. The other two differences are the use of shift registers and the inclusion of a touch screen. These two differences are a large chunk of the reason I am opting for a ground up approach rather than QMK or ZMK.

# LVGL
The first headache of this project was setting up the screen. I haven't managed to find a touch screen with the right aspect ratio yet but for now I am working with a TFT screen from Adafruit. Setting up the drivers was pretty straight forward until it wasn''t. There are several libraries for the Arduino and CircuitPython to work with the driver I am using (ST7735R) but nothing I found was made for the Pi Pico. I more or less cloned the existing logic into C and then spent several days fixing the differences. It boiled down to making sure the sequence of boot commands was called in the correct order. This was a bit of a challenge as the different libraries were generally designed for multiple different drivers and had a lot of code to accomodate changes. Once that was working it was time for the second headache: LVGL.

LVGL is a graphics library for embedded systems. I opted to use it cause when I Googled libraries for embedded systems it popped up first...

The documentation is pretty good if you actually read it, but I made the mistake of experimenting with ChatGPT to see how well it could write it for me. It did a decent job but I spent a lot of time poking and probing to understand what it was doing. Ultimately I read the documentation and it more or less walked through all the necessary functions and I got LVGL running.

# Shift Registers

The registers were a challenge in their own right. The resolution for this also came from reading the documentation. The timing to shift in data and the set of pins that should be high were clearly explained so it was only a matter of a few doxen lines of C to ensure that things were read in correctly. 

One issue I am currently dealing with is bleed between the pins. Theres a pair of inputs on the register that only fire together which is kind of bizarre. I've chained two registers together and it worked out alright so I don't think it's a software issue. I decided it was the cheap breadboard I was using and went ahead and ordered a few pcbs with enough space for 2 registers and 16 keys. I'm hoping having it on the PCB will eliminate any issues from faulty wiring or loose connections on the bread board.

### Edit:
In the time between when I first started drafting this post and now, I figured out the issue! To shift data from the register you have to trigger the pins in a very specific sequence to store the data and then shift it one by one into the output pin. I had the sequence slightly shifted so it never actually read the first pin. On the second iteration of the loop it read the bits that were set for both the first and second input, thus causing the bleed!
{{<raw>}}
<div style="display: flex; flex-direction: row;">
<div style="width: 50%">
<img src="../imgs/registers_before.png" alt="Initial Code" style="height:40vh; width: auto;">
<figcaption style="text-align: center;">Initial Code</figcaption>

</div>
<div style="width: 50%">
<img src="../imgs/registers_after.png" alt="Fixed Code" style="height:40vh; width: auto;">
<figcaption style="text-align: center;">Fixed Code</figcaption>

</div>
</div>
{{</raw>}}
<!-- 
![Initial Code](../imgs/registers_before.png "Initial Code")
![Fixed Code](../imgs/registers_after.png "Fixed Code") -->

