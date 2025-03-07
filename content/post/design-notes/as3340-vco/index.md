---
title: "AS3340 VCO"
description: 
date: 2023-12-29T00:00:00+08:00
image: 
categories:
    - Design Notes
tags:
    - VCO
    - Eurorack Module
    - Oscillator
    - Analog
    - Electric Druid
status: To build prototype, incomplete design notes
---

## Resources

- [Tri to sin using a JFET](https://www.timstinchcombe.co.uk/index.php?pge=trisin)
- [AS3340 Datasheet](http://www.alfarzpp.lv/eng/sc/AS3340.pdf)
- [Electric Druid - 3340 VCO Designs](https://electricdruid.net/cem3340-vco-voltage-controlled-oscillator-designs/)
- [YuSynth VCO](https://yusynth.net/Modular/EN/VCO/index.html)
  
## AS3340 Chip breakdown

### Power Supply

- Pins 16 (VCC Positive) and 3 (VEE negative)
- CANNOT be powered with +/- 15V, +/-12V without protection
- Voltage between VCC and VEE should be less than +24V
- Voltage between VCC and GND should be less than +18V
- Voltage between VEE and GND should be less than -6V
  - A current limiting resistor is used in the datasheet when powering it with -15V
  - You can power VEE with -5V without using a current limiting resistor
  - When powering VEE with -15V, use an 820R current limiting resistor
  - When powering VEE with -12V, use a 470R current limiting resistor

### Sync

- Pins 6 (Hard SYNC) and 9 (Soft SYNC)

### Output Levels

- Pins 4 (Pulse), 8 (Saw), and 10 (Triangle)
- Ramp - 2/3rds of the positive supply
- Triangle - 1/3rd of the positive supply
- Pulse - positive supply minus 1.3V
  - Open emitter - requires a pulldown resistor to set the lower level
- With a +15V supply
  - Ramp - 0 to 10V
  - Triangle - 0 to 5V
  - Pulse - 0 to 13.5V
- With a +12V supply
  - Ramp - 0 to 8V
  - Triangle - 0 to 4V
  - Pulse - 0 to 10.7V

### Scale pins

- Pins 1 (Scale1) and 2 (Scale2)
- For temperature compensation

### High frequency tracking

- Pin 7
- Compensates for the way that the time taken for the internal comparator to switch becomes significant at higher frequencies

### Timing capacitor

- Pin 11
- Use a good quality capacitor
- Low leakage, low tempco
- Polystyrene film is the best option
- 1nF value

### Linear FM input

- Pin 13
- Sometimes not used by designers, a only bias network is present (1M5, 470R, 10n)

### Note CV (Frequency CV) input

- Pin 15
- a virtual ground summing node
- Usually see a bias network (360K, 470R, 10n)
- Summing resistors connected to the node for CV sources
