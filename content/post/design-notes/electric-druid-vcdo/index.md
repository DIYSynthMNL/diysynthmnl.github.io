---
title: "Electric Druid VCDO"
description: 
date: 2023-12-29T06:07:14Z
image: 
categories:
    - Design Notes
tags:
    - VCO
    - Eurorack Module
    - Oscillator
    - Digital
    - Wavetable
    - Electric Druid
status: Prototype built, incomplete design notes
---

- [x] Draw schematic based on the datasheet
- [x] Determine if the regulators need load resistors, I’ll put it in just in case
- [x] Try to change the CV input op amps to MCP6004 compare both
- [x] TL074 will suffice
- [x] Add bitcrush CV in
- [x] Add glide CV in
  
### Adding CV to bitcrush and glide

The circuit below converts 10vpp +/-5v to 0-5v using a TL074 op amp

![10vpp_to_5v](10vpp_to_5v.png)

The circuit below does the following. When you plug in a 10vpp signal, it will bypass RV14, the control pot. When there is nothing plugged in, you can control the parameter using the potentiometer.

![10vpp_to_5v_circuit_2](10vpp_to_5v_circuit_2.png)
  
The screenshot below is a simulation of the circuit above.

![10vpp_to_5v_circuit_2_sim](10vpp_to_5v_circuit_2_sim.png)
  
- [x] Take a look at the circuit from Electric Druid’s LFO. We wouldn't need the circuit above.
  
A much better circuit for glide and bitcrush

![10vpp_to_5v_circuit_final](10vpp_to_5v_circuit_final.png)
