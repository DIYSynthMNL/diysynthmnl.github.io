---
title: "AS2164 Quad Exponential VCA"
description: A Quad Exponential VCA Module based on the AS2164 chip
date: 2023-12-29T06:07:14Z
image: images/DSC06842.jpg
categories:
    - Design Notes
tags:
    - VCA
    - Eurorack Module
    - Amplifier
    - Analog
    - Electric Druid
status: Prototype built, incomplete design notes
---
[Module GitHub Repo](https://github.com/DIYSynthMNL/Eurorack-2164-Quad-Exponential-VCA)

## TODO

- [x] Schematic
- [x] Prototype
- [ ] PCB Design

## Introduction

This module is a simple Quad VCA design. The design is based on the chip’s datasheet info.

## Module Images

![Front](images/DSC06842.jpg)

![Back](images/DSC06846.jpg) ![Side](images/DSC06847.jpg)

## Demo

{{< youtube t1I3HN3v_0g >}}

## Module Features

Four exponential voltage controlled VCAs.

Each CV input is normalled to the next. CV1>CV2>CV3>CV4
Each Signal input is normalled to the next. IN1>IN2>IN3>IN4

The 4th output jack can be switched to either the 4th VCA output or the mix output using a jumper.

## I/O and Controls

Each VCA channel will have:

- Control voltage input (10vpp)
- Input attenuation knob
- Control (when no cv) / offset knob (when cv signal is present)
- Signal input (audio or CV signals)
- Signal output

## Design Notes

### Designing the cv input circuit

[https://www.analog.com/media/en/technical-documentation/data-sheets/SSM2164.pdf](https://www.analog.com/media/en/technical-documentation/data-sheets/SSM2164.pdf)

Control voltage and gain/attenuation

- Unity gain = 0v control voltage
- -100dB of attenuation = +5v control voltage

With that, a control voltage of 0 to 5v is optimal. We can just invert the input using an inverting op amp.

Another design decision that I would like to add to the module is normalling both cv and audio inputs to the next vca. I1>I2>I3>I4, CV1>CV2>CV3>CV4 when nothing is connected to multiply whatever is connected to the first input.
  
![2164_power_rail_failure](2164_power_rail_failure.png)

Protection from no negative power supply

![2164_cv_to_db_range](2164_cv_to_db_range.png)

### Using the SSI 2164 datasheet CV input circuit

![0_to_5v_exponential_control_circuit](0_to_5v_exponential_control_circuit.png)

2164 chip voltage and attenuation relationship (Inverse) based on the ssi2164 datasheet

- 3.4V = Mute
- 0V = unity gain
Datasheet circuit
- sums, inverts, attenuates the control voltage input

### Falstad simulation link

[Falstad Link](https://github.com/DIYSynthMNL/Eurorack-2164-Quad-Exponential-VCA/tree/main/falstad)

### Resources

- [http://www.sdiy.org/philgallo/mgbvca.html](http://www.sdiy.org/philgallo/mgbvca.html)
- [https://doepfer.de/a1324.htm](https://doepfer.de/a1324.htm)
- [https://modwiggler.com/forum/viewtopic.php?t=96486](https://modwiggler.com/forum/viewtopic.php?t=96486)
- [http://electronic-sea.net/SSM2164.html](http://electronic-sea.net/SSM2164.html)
- [https://www.amazingsynth.com/parts/ssi2164/ssi2164-datasheet.pdf](https://www.amazingsynth.com/parts/ssi2164/ssi2164-datasheet.pdf)

## Schematic

![Schematic](images/Eurorack-2164-Quad-Exponential-VCA-Schematic-Rev0.1.4.jpg)

## Conclusion

If you'd like to build this module, I have provided a 3D printed front panel file in the repo. I used readily available green perfboard. The components should line up with the perfboard's holes. The panel was made using benjiaomodular's [europanelmaker](https://github.com/benjiaomodular/EuroPanelMaker).
