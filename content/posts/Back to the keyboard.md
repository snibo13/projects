---
title: "Back to the keyboard!"
date: 2023-06-18T09:42:35-07:00
draft: false
list: true
color: "#C57B57"
summary: 
---

Back in 2021 I made a seven key [macropad](../brevis/) with an encoder knob using QMK. The original goal with that project was to serve as a trial case for building a fullsized (or at least 65%) keyboard. Two years later, I'm finally getting around to it. I took so long because I was

The design I'm going with is largely inspired by a collection of tweets by [Claudio Guglieri](https://twitter.com/claudioguglieri). 

Here are a couple:
{{< raw >}}
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">More keyboard renders with touch display and led keycaps. <a href="https://t.co/lJBygeG31V">pic.twitter.com/lJBygeG31V</a></p>&mdash; Claudio Guglieri (@claudioguglieri) <a href="https://twitter.com/claudioguglieri/status/1663824909087440896?ref_src=twsrc%5Etfw">May 31, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
{{< /raw >}}
{{< raw >}}
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Scroll scroll scroll 🔁 <a href="https://t.co/m7Ccu8LLiT">pic.twitter.com/m7Ccu8LLiT</a></p>&mdash; Claudio Guglieri (@claudioguglieri) <a href="https://twitter.com/claudioguglieri/status/1660903186482495489?ref_src=twsrc%5Etfw">May 23, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
{{< /raw >}}
It's more or less a rethinking of the old touchbar but I think the design is really nice and I'm largely doing it as an excercise. I don't think the inclusion of the screen will be a game changer for my productivity or anything but it looks cool and adds some complexity to the project.

I'm also toying with the idea of adding a IR array for gesture detection off the side but that's still uncertain.

One other source of inspiration is the [HelloWord keyboard](https://github.com/peng-zhihui/HelloWord-Keyboard) by Peng Zhihui. Rather than using the traditional matrix scanning for reading key states he uses a collection of shift registers. This means infinite-key rollover and a sampling time as fast as you can flip a clock signal. With my typing speed of 101 words per minute I definitely need a sampling rate in the Megahertz.

This is what I'm currently prototyping with:
- Raspberry Pi Pico (I'm considering switching to the Pico W so I can play around with some WiFi stuff or add bluetooth support)
- SN74HC165N: This is an 8 parallel input serial output shift register
- TFT display with ST7735R driver

The biggest unknown right now is the display. It's proving difficult to find a touch screen display with the aspect ratio that I'm looking for but I'm still on the hunt. Right now I'm working on some firmware to read the inputs from the shift register and an LVGL driver for the st7735r. I opted to go for the Pi Pico SDK rather than using Arduino so I could get a better understanding of embedded system development. You can expect a post about that at some point to.

That's all for now. Cheers.