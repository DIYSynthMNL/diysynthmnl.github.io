---
title: "Kikit Multiboard Workflow"
description: 
date: 2025-03-06T18:12:43Z
image: 
categories:
    - Quick Tips
tags:
    - KiCad
    - PCB
    - Workflow
    - Multiboard
---

KiCad terminal Command

```Python
kikit separate --source "annotation; ref: B3" ^ "C:\Users\Acer\Desktop\Synth DIY\KiCad Designs\EuroBusboard\EuroBusboard.kicad_pcb" "C:\Users\Acer\Desktop\Synth DIY\KiCad Designs\EuroBusboard\eurobusboard_jst_8.kicad_pcb"
```

How to use it?

1. Open KiCad Command Prompt
2. Enter the command

```Python
kikit separate --source "annotation; ref: [Board marker reference (ex. A)]" ^ 
"[Path to .kicad_pcb to separate]" "[Path to save separated .kicad_pcb]"
```
