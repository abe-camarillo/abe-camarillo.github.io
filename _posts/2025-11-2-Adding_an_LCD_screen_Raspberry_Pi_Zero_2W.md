---
layout: post
title:  "An attempt to add a TFT screen to my Raspberry Pi Zero 2W"
date:   2025-11-2 19:47:26 -0600
categories: jekyll update

---

Recently I started checking some boxes were I had assorted PCBs lying around of my old projects, and I found some Raspberry Pis I bought some time ago. I didn't have a clear idea what purpose to give them, so I store them while I think of something. It usually is a paralysis by analysis scenario, where the little computers have so much potential, that any project that I could some up to seems plain and boring. So they end up stored in these boxes collecting dust.

Fortunately today was not the case, and I just ended up flashing some recent version of Raspberry Pi OS, inserted the SD card in place, and tried to boot the system. It was nice to thinker up different versions of Raspberry Pi just to pass the time and see which improvements the Raspberry Pi Foundation has come up to in the recent months. The Raspberry Pi OS keeps being polished and seems easier to use nowadays.

### Connecting the LCD screen to the Raspberry Pi

But the thing that made me write this entry was trying to come up with a way to use an LCD screen I had lying around, that was intended to show some dynamic images or videos. In my mind, it seemed easier to do this with the Arduino, but then I realized the micro-controller is not that powerful and likely would need something more beefy, like the ESP32 or the Raspberry Pi Pico. But since I haven't coded something low level recently, I wasn't very attracted to try it for some time.

This time though, I was able to find an ILI9341 driver in GitHub, after asking around to Perplexity.ai, ready for the Raspberry Pi. And it was quite old, but I decided to try to compile it since the logic seemed straightforward, and see how it went. The reason to use this old driver is because my shield didn't have the SPI interface, so I had to use a parallel port driver. The most commonly used and frequently supported driver uses this interface. So I have 5 pins for commands, and the other 8 are for the data, the goal was to initialize and send the pixel data through the 8 pins.

![Raspberry Pi connected to the LCD screen](/pictures/raspberry_conexion.jpeg)

### Building the ILI9341 module

The first time it did not work, because it was targeted for an older kernel that removed some flags, and there were some unused methods that raised warnings at the compiling time. I tried using perplexity to fix the error codes, and this time it built, but when I tried installing the module, it caused an error with the kernel. After several reboots and bumping my head on the wall, I decided to install Cursor, and use the free tier to improve the code, by making a fork into my Github account and cloning the repository in my Raspberry.

After some adjustments and quick feedback with Cursor's chat, I managed to get a working version that allowed me to send some data to the `/dev/fb0` device, so I could get a picture displayed on the screen.

The downside is that it seems this hardware is inherently constrained, because of the OS calls, it ends up being slower than using a board with SPI protocol. So maybe I won't be able to get something faster than 10 fps, and displaying a video stream is not that viable. Still, it was nice to try and build an external module that allowed me to communicate with the ILI9341. It appears to be easier than I thought, because I didn't know you could build your own modules and install them in the Linux kernel.

![LCD screen showing a picture loaded with the python script](/pictures/LEGO_brick_raspberry.jpeg)

### Conclusions

So long story short, I got the module installed, and the screen showed a picture using a Python script. I learnt a little more about Linux drivers/modules and how you can build your own and install them in the kernel. Building modules seems a little less obscure than I thought, and the building requirements are a less complex than I expected.

It is indeed risky to do it without documenting yourself a little, and with some word of caution; because you can get segmentation faults, and break something quite easily. So memory management, and knowing how to handle the modules properly is also important. Quite luckily, I found and interesting guide that was recently updated, regarding how to build modules for the Linux kernel. So I gave it a read, and know I'm a little more informed on how to proceed carefully and what to avoid.

Also, working with Cursor for these less popular/diffused tasks is amazingly easier. I remember trying to learn kernel things when I was younger, and the documentation at the time didn't make sense to me at all. I also didn't know as much of programming as I do now, which explains it. But with AI tools, the complexity is manageable, and we just need to ask around and it will give you appropriate resources. So we just need to be careful, try things gradually so you don't break something drastically, and preferably in a smaller system like the Raspberry Pi. But even if you do, that's the purpose of the Raspberry, right? To learn more about your computer in a cheaper, somewhat disposable system.

---
Useful links:

[The original ILI9341 driver module](https://github.com/sammyizimmy/ili9341/tree/master)

[My own fork of the ILI9341 driver](https://github.com/abe-camarillo/ili9341)

[The Linux Kernel Module Programming Guide](https://sysprog21.github.io/lkmpg/)
