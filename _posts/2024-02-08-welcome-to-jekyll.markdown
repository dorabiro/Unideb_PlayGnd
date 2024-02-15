---
layout: post
title:  "Sallen-Key Filter"
date:   2024-02-08 17:28:23 +0100
categories: jekyll update
math_engine: mathjax
use_math : true
---
In this post you can read about a special case of the general [Sallen-Key][sallen-key] topology, where equal resistor and capacitor values were used:  `R1 = R2 = R` and `C1 = C2 = C`. In the following you can find the tools, results, and methods which I used.

**Used instruments:**

  -  Oscilloscope RIGOL DS1074 Z+
  -  Function generator RIGOL DG1032Z
  -  Power supply GWInstek GPD3303S

**Used components:**

    U1 = LM358
    U2 = OP482
    R1 = R2 = R4 = R5 = 10kΩ
    R3 = 1kΩ
    C1 = C2 = 10nF
    C3 = C4 = 47uF

**Measurement parameters:**

    Frequency range: 10 Hz - 10 kHz
    Signal waveform: sinusoidal
    Output signal level: 5 Vpp
    IC supply voltage: ±12 V


**Used software and packages:**

    KiCAD
    LTSpice
    SciLab
    Python PyVISA-Py"


<img src="/unideb.playgnd/images/breadboard.png" alt="Picture not found">
<p align="center" style="font-size: 18px;">
Circuit on breadboard</p>

**System Identification**

To understand the selected system, it is necessary to determine the mathematical relationship among its characteristics, the equations governing these characteristics, and the coefficients within them. Overall, during the completion of the task, structural and parameter identification was conducted.

When $$(a \ne 0)$$, there are two solutions to $$(ax^2 + bx + c = 0)$$ and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

 - but its not working yet.





{% include codeHeader.html %}
```python
for i in range(FREQ_STEPS):
    # Reset oscilloscope statistics
    scope.write(':MEASure:STATistic:RESet')
    # Calculating the frequency step
    output_Freq = 10**(((math.log10(STOP_FREQ)-math.log10(START_FREQ))/(FREQ_STEPS-1)*(1+i-1))+math.log10(START_FREQ))
    
    # Set horizontal scale
    if horizontalScale != getHorizontalScale(output_Freq):
        horizontalScale = getHorizontalScale(output_Freq)
        scope.write(':TIMebase:SCALe ' + str(horizontalScale))
    # Set frequency
    fgen.write(':SOURce1:FREQuency ' + str(output_Freq))
    time.sleep(1)
    # Reading and calculating data
    ch1_Frequency = float(scope.query(':MEASure:STATistic:ITEM? AVERages,FREQuency,CHANnel1'))
    ch1_Voltage = float(scope.query(':MEASure:STATistic:ITEM? AVERages,VPP,CHANnel1'))
    ch2_Voltage = float(scope.query(':MEASure:STATistic:ITEM? AVERages,VPP,CHANnel2'))
    ch_Phase = float(scope.query(':MEASure:STATistic:ITEM? AVERages,RPHase'))*-1
    calc_dB = 20*math.log10(ch2_Voltage/ch1_Voltage)
    dat_Freq.append(ch1_Frequency)
    dat_dB.append(calc_dB)
    dat_Phase.append(ch_Phase)
    # Set horizontal scale
    if verticalScale2 != getVerticalScale(ch2_Voltage):
        verticalScale2 = getVerticalScale(ch2_Voltage)
        scope.write(':CHANnel2:SCALe ' + str(verticalScale2))

# Close instruments
fgen.write(':OUTPut1:STATe OFF') # Turn off the fgen output
scope.close()
fgen.close()
rm.close()
```


[sallen-key]: https://en.wikipedia.org/wiki Sallen%E2%80%93Key_topology
