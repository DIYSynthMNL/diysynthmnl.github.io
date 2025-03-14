---
title: "AS3320 VCF"
description: 
date: 2023-12-29T06:07:14Z
image: images/DSC06861.jpg
categories:
    - Design Notes
tags:
    - VCF
    - Eurorack Module
    - Filter
    - Low Pass Filter
    - Analog
    - Electric Druid
status: Prototype built, incomplete design notes
---

[Module GitHub Link](https://github.com/DIYSynthMNL/Eurorack-3320-VCF)

## TODO

- [x] Schematic
- [x] Prototype
- PCB Design

## Introduction

This module is a Low Pass VCF using the AS3320 chip I bought from Electric Druid.

## Module Images

![Front](images/DSC06861.jpg)

![Back](images/DSC06863.jpg) ![Side](images/DSC06864.jpg)

## Demo

{{< youtube V5NmFUjbHUY >}}

## Module Features

## Design Notes

### Resources

- [V3320 datasheet from cool audio](https://www.coolaudio.com/docs/Cool%20Audio_Data_Sheet_V3320_VCF.pdf)
- [AS3320 datasheet](https://electricdruid.net/wp-content/uploads/2017/06/AS3320.pdf)
- [Electric Druid's article about cem3320 filter designs](https://electricdruid.net/cem3320-filter-designs/)
- [Electric Druid article about reconfigurable filters](https://electricdruid.net/multimode-filters-part-1-reconfigurable-filters/)
- [Electric Druid article about pole mixing filters](https://electricdruid.net/multimode-filters-part-2-pole-mixing-filters/)
- [Eddy Bergman's digisound 80 build](https://www.eddybergman.com/2020/03/synthesizer-build-part-23-digisound-80.html)
- [Hagiwo’s circuit](https://note.com/solder_state/n/n372399e1a0f2)

### Reddit help question

> Eurorack 3320 Low Pass VCF Design Help Needed: Electrolytics for AC Coupling? And some other design questions.
>
>![ac_coupling_cap](ac_coupling_cap.png)
>
>Hi there! I’m designing a Eurorack 3320 LP VCF based on the AS3320 chips I got from Electric Druid. I’ve tried my best to research before asking here but I came up sort of knowledge. I’d like to ask for your help! I’ve got a small quantity of these AS chips and I want to build them into Eurorack modules as correct as possible.
>The datasheet for the 3320 uses an electrolytic cap on its output. I’ve read that there are downsides when using (polarized capacitors) [electrolytics for AC coupling](https://northcoastsynthesis.com/news/electrolytics-for-ac-coupling/).
>One suggestion that the article said is this: “Use two polarized electrolytic capacitors back to back, with or without some kind of DC bias applied to the centre, or parallel diodes that attempt to limit reverse voltage.”
>I’m not quite sure what’s the best way to handle this.
>[My current schematic](https://github.com/DIYSynthMNL/Eurorack-3320-VCF/blob/main/Schematic%20PDFs/3320-VCF-Schematic-Rev0.1.0.pdf) applying the two polarized capacitors back to back.
>Some other questions that popped up in my head:
>
>1. Based on the datasheet circuit, the output of the 3320 is DC (0V to VCC*0.43)?
>2. Should the 3320’s audio input be AC coupled as well?
>3. What voltages does the 3320 expect at its audio inputs?
>4. Circuits I saw online have inverting buffers before the 3320’s audio input. Why is this necessary? Why invert them?
>  
>I appreciate the help!
>
>u/halifax's reply:
>
>1. The datasheet shows an output DC offset of between 5 V to 9 V with a typical value of 6.5 V with +-15V supply and 0 V input.
>2. I haven't seen AC coupling on the Mutable Ripples or Befaco BF-22. It seems that the common practice is to not AC couple for general inputs in Eurorack low pass filters.
>3. The 3320 input is basically an Operational Transconductance Amplifier (OTA) which has a current input. Pin 1 is basically at ground. There is a hard current limit on the chip of 40mA for any pin. With the 91k input resistor and assuming a +-5V VCO input you get a really small current of around +- 0.055 mA.
>4. Generally you want to keep your pass band (e.g. the part below the cutoff of a low pass) to be in phase with your original signal. If you are looking at snippets of some larger schematic there may be an inverting stage upstream that they are inverting back from. Something like an inverting mixer that combines a few signals that needs to be inverted back again so that the output is in phase with the input signal.
>On your schematic I would only include the AC coupling before the Pro-one output buffer and since you know that it's positively biased you don't need the back-to-back caps. The feedback signal needs to be AC coupled. I would skip the inverter input, input AC coupling and change the output inverter to a buffer and get rid of that AC coupling since that is handled in the previous stage.

## Schematic

![Schematic: core](images/3320-VCF_Schematic-Rev-0.1.5_3.jpg)

![Schematic: controls](images/3320-VCF_Schematic-Rev-0.1.5_2.jpg)

## Conclusion

If you'd like to build this module, I have provided a 3D printed front panel file in the repo. I used readily available green perfboard. The components should line up with the perfboard's holes. The panel was made using benjiaomodular's [europanelmaker](https://github.com/benjiaomodular/EuroPanelMaker).
