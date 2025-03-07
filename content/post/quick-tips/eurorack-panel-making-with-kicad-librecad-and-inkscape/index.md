---
title: "Eurorack Panel Making With KiCad, LibreCad, and Inkscape"
description: 
date: 2023-12-27T00:00:00+08:00
image: 
categories:
    - Quick Tips
tags:
    - KiCad
    - PCB
    - Workflow
    - LibreCad
    - Inkscape
    - Eurorack Panels
---

## My workflow on making Eurorack front panels

1. Lock footprints on control board where the controls are soldered by using the lock feature in KiCad so that they won’t be moved when placing the panel hole footprints.
2. Make the panel board outline. Be sure to align it with the control board. The footprints of the control board should be locked or else you’ll have a hard time moving the panel board out of the control board.
3. Place panel hole footprints on the control board footprints. Alignment points on the panel hole footprints should snap to the control board footprints.
4. When finished placing panel hole footprints. Triple check alignment then highlight the whole front panel and move it out of the control board. Make sure that the locked footprints are not selectable - unselect locked footprints check box in selection filter.
5. To make it easy to make the front panel graphics, I use LibreCad to mark holes and clearances for the graphics. In KiCad, you will use the dimension tool to mark where the holes are and then transfer it manually to LibreCad. I’ll explore exporting to svg in kicad soon.
6. Next I’ll import the hole guide svg to inkscape to place front panel graphics.
7. Use black for the objects and paths, use white for the background.
8. Convert all objects to paths (text are objects). This is important because KiCad can’t render those objects.
9. Keep the board outline, you’ll need it for alignment later in KiCad.
10. The svg created in Inkscape should be ready for importing.
11. Import the svg by clicking file > import > graphics (ctrl + shift + F) and import your svg file.
12. Double click the front panel graphics and make the layer front silkscreen.
13. Align the graphic to the front panel board outline.
