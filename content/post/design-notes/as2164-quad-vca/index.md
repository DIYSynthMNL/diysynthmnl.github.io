---
title: "AS2164 Quad Exponential VCA"
description: A Quad Exponential VCA Module based on the AS2164 chip
date: 2023-12-29T06:07:14Z
image: 
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
## Designing the cv input circuit

[https://www.analog.com/media/en/technical-documentation/data-sheets/SSM2164.pdf](https://www.analog.com/media/en/technical-documentation/data-sheets/SSM2164.pdf)
  
Control voltage and gain/attenuation

- Unity gain = 0v control voltage
- -100dB of attenuation = +5v control voltage

With that, a control voltage of 0 to 5v is optimal. We can just invert the input using an inverting op amp.

![cv_input_circuit](cv_input_circuit.png)
  
Another design decision that I would like to add to the module is normalling both cv and audio inputs to the next vca. I1>I2>I3>I4, CV1>CV2>CV3>CV4 when nothing is connected to multiply whatever is connected to the first input.
  
![2164_power_rail_failure](2164_power_rail_failure.png)

Protection from no negative power supply

![2164_cv_to_db_range](2164_cv_to_db_range.png)

![hagiwo_2164](hagiwo_2164.png)

Hagiwo’s design.

## Using the SSI 2164 datasheet CV input circuit

![0_to_5v_exponential_control_circuit](0_to_5v_exponential_control_circuit.png)

2164 chip voltage and attenuation relationship (Inverse) based on the ssi2164 datasheet

- 3.4V = Mute
- 0V = unity gain
Datasheet circuit
- sums, inverts, attenuates the control voltage input

## Resources

- [http://www.sdiy.org/philgallo/mgbvca.html](http://www.sdiy.org/philgallo/mgbvca.html)
- [https://doepfer.de/a1324.htm](https://doepfer.de/a1324.htm)
- [https://modwiggler.com/forum/viewtopic.php?t=96486](https://modwiggler.com/forum/viewtopic.php?t=96486)
- [http://electronic-sea.net/SSM2164.html](http://electronic-sea.net/SSM2164.html)
- [https://www.amazingsynth.com/parts/ssi2164/ssi2164-datasheet.pdf](https://www.amazingsynth.com/parts/ssi2164/ssi2164-datasheet.pdf)
