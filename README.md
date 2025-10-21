# GlasgowICAdapter
I wanted an adapter board to be able to use my ICs with my Glasgow Interface Explorer, without having to manually connect the leads one by one.

# On the design
The design, by default, uses four [TMUX1209](https://www.ti.com/lit/ds/symlink/tmux1208.pdf) Dual-Channel Multiplexers, which allows the Glasgow to communicate with ICs with up to 32 pins, whilst retaining a high speed, and still have four IOs left for general use. But, the objective of this board is to be *flexible*. And some chips don't just need digital IO, some need analog inputs and/or outputs, and some others even need higher speeds, if with less pins. For these reasons, you can disable each one of the four multiplexers individually with the EN_Ux bridges. When these pins are bridged, the appropiate multiplexer's outputs will be disabled, and you can use the breakout besides each of the two ports, in combination with the ZIF socket breakout, and some jumper cables, in order to properly connect everything as you need it.

# On the multiplexers
The multiplexers are wired 2-on-2 to each port. Four pins serve as the signal IOs (2,3,4,5), whilst two other pins (0,1), serve as the address selectors, which are wired so that both multiplexers on each channel share these address pins. The enable pins of the multiplexers are pulled up by one 10kOhm resistor each, and can be grounded by using its respective EN_Ux jumper. These multiplexe2rs support 1.8V logic, and are wired directly into the VIO of their respective port. This allows them to work with the full voltage range of the Glasgow.
