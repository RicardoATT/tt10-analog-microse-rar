<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

There are 2 different implementations of spiking neurons and a biological synapse circuit, all sharing the same inputs, but with independent outputs. The operation of each circuit is described below:

### Richmond's Synapse:

### Ricardo's Neuron:
The circuit implements a leaky integrate-and-fire (LIF) neuron, requiring a voltage input at *Vin0* (**ua[0]**) to charge capacitor *C1*, which emulates the membrane behavior of a biological neuron. The charging rate depends on the applied stimulus. Once a threshold is reached, a Schmitt trigger generates a spike, and with the assistance of a reset circuit, a spike is produced at the output Vout_ratt (ua[4]).

To modulate the pulse frequency, it is necessary to apply a stimulus to the *Vin1* (**ua[1]**) terminal. Within a voltage range of 0 - 1.8 V, a higher voltage results in a higher spike frequency. Additionally, the *Vin2* (**ua[2]**) terminal must be stimulated to discharge *C1* when no input stimulus is present. This leakage influences the output spike frequency and spike width, although to a lesser extent.

### Abraham's Neuron:

## How to test

Each circuit has its own way of being tested, so below is a description of each one:

### Richmond's Synapse:

### Ricardo's Neuron:
- Stimulate *Vin0* to charge *C1* and generate spikes at the output Vout_ratt. A stronger stimulus results in a higher spike generation rate at the output.
- Stimulate *Vin1* to modulate the output spike frequency. A stronger stimulus increases the spike frequency.
- Stimulate *Vin2* to adjust the inherent leakage in the neuron's charge. A stronger stimulus increases the capacitor's discharge rate, delaying spike generation and thus altering the output frequency.
>[!TIP]
>
>Adjust the stimuli at all three inputs to observe the different effects on the output.

### Abraham's Neuron:

## External hardware

All circuits require the use of the following hardware:
- Oscilloscope.
- Power supply.
- Function generator.
