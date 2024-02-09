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



You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter.  

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[sallen-key]: https://en.wikipedia.org/wiki Sallen%E2%80%93Key_topology
