---
layout: post
title:  "Sallen-Key Filter"
date:   2024-02-08 17:28:23 +0100
categories: jekyll update
---
In this post you can read about a special case of the general [Sallen-Key][sallen-key] topology, where equal resistor and capacitor values were used:  `R1 = R2 = R` and `C1 = C2 = C`. In the following you can find the tools, results, and methods which I used.

Used instruments:

  -  Oscilloscope RIGOL DS1074 Z+
  -  Function generator RIGOL DG1032Z
  -  Power supply GWInstek GPD3303S

Used components:

    U1 = LM358
    U2 = OP482
    R1 = R2 = R4 = R5 = 10kΩ
    R3 = 1kΩ
    C1 = C2 = 10nF
    C3 = C4 = 47uF

Measurement parameters:

    Frequency range: 10 Hz - 10 kHz
    Signal waveform: sinusoidal
    Output signal level: 5 Vpp
    IC supply voltage: ±12 V

Used software and packages:

    KiCAD
    LTSpice
    SciLab
    Python PyVISA-Py"


[sallen-key]: https://en.wikipedia.org/wiki Sallen%E2%80%93Key_topology

![Breadboard](/assets/breadboard.png)