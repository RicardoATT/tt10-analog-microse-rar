<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

There are 2 different implementations of spiking neurons and a biological synapse circuit, all sharing the same inputs, but with independent outputs. The operation of each circuit is described below:

### Richmond's Synapse:
This project implements an electronic synapse using NMOS and PMOS transistors. The design allows the circuit to either supply or drain current, mimicking the behavior of biological synapses. Additional MOS are integrated to to fine-tune the supplied or drained current and have a greater control over the operation of the synapse.

The synapse has the following input/output pins (not taking into consideration vdd and gnd)
Synapse_Input: Accepts input from a spiking neuron or a digital signal from digital circuitry, with a voltage range of 0.9V to 1.8V.
- Inhibitory_current_control: Regulates the amount of current supplied by the synapse.
- Excitatory_current_control: Regulates the amount of current supplied by the synapse.
- Synapse_control: Determines whether the synapse acts as excitatory or inhibitory, when activated with a digital signal, it selects either excitatory or inhibitory behavior; when provided with an analog signal, it enables intermediate behavior, allowing a graded response at the cost of higher power consumption.
- Synapse_output: Outputs the synapse’s response, capable of push-pull operation between VDD and GND, as well as intermediate voltage levels.

### Ricardo's Neuron:
The circuit implements a leaky integrate-and-fire (LIF) neuron, requiring a voltage input at *Vin0* (**ua[0]**) to charge capacitor *C1*, which emulates the membrane behavior of a biological neuron. The charging rate depends on the applied stimulus. Once a threshold is reached, a Schmitt trigger generates a spike, and with the assistance of a reset circuit, a spike is produced at the output Vout_ratt (ua[4]).

To modulate the pulse frequency, it is necessary to apply a stimulus to the *Vin1* (**ua[1]**) terminal. Within a voltage range of 0 - 1.8 V, a higher voltage results in a higher spike frequency. Additionally, the *Vin2* (**ua[2]**) terminal must be stimulated to discharge *C1* when no input stimulus is present. This leakage influences the output spike frequency and spike width, although to a lesser extent.

### Abraham's Neuron:

## How to test

Each circuit has its own way of being tested, so below is a description of each one:

### Richmond's Synapse:
- To test an inhibitory synapse the Inhibitory_current_control has to be set to 0v, Excitatory_current_control has to be set to 0v, the Synapse_control has to be set top 1.8v.

- To test an excitatory synapse the Inhibitory_current_control has to be set to 1.8v, Excitatory_current_control has to be set to 1.8v, the Synapse_control has to be set top 0v.

- When modifying the current of each synase the voltage of said synaopse varies 

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
