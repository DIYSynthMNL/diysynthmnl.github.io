---
title: "Protecting Digital IO From Eurorack Levels"
description: So you want to design a module with Arduino or other low voltage digital devices and you don’t know how you’ll protect them.
date: 2025-03-06T15:33:17Z
image: cover.jpg
---
So you want to design a module with Arduino or other low voltage digital devices and you don’t know how you’ll protect them. Here’s some circuits to help you.


# CV input with attenuation to analog Arduino inputs (A0, etc.)

Using Mutable Instruments’ Grids as our first example:

![cover.jpg](cover.jpg)

- You will need a rail to rail op amp. A popular choice would be an MCP6002 chip.
- The output of the op amp connects to an analog input of an Arduino.
- You would need a negative reference voltage source. Grids used a Zener diode. VEE is -12v.
- The op amp would be powered by 5v and ground.
