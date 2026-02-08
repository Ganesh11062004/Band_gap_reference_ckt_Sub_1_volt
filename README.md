## CMOS Bandgap Reference Circuits – UMC 180 nm

This repository contains the design, implementation, and simulation of three CMOS Bandgap Reference (BGR) circuits developed in UMC 180 nm technology.
The objective of this project is to analyze temperature stability, supply sensitivity, and low-voltage operation, and to compare different BGR architectures.

All circuits were designed and verified using Cadence Virtuoso with DC, temperature sweep, and supply variation simulations.

# Circuit 1: Current-Mirror-Based Bandgap Reference

This design implements a classical current-mirror-based bandgap reference, combining PTAT and CTAT components to generate a temperature-compensated reference voltage.
The circuit serves as a baseline architecture and highlights the limitations of mirror-only designs in terms of temperature sensitivity and supply dependence.
![](https://github.com/Ganesh11062004/Band_gap_reference_ckt_Sub_1_volt/blob/65724329e82c10e639391d6a2c5a0a02bfa5d60e/schematic_ckts/bgr_currmirr.png)

### Performance Summary
+ Reference Voltage (Vref) = 1.28V at 27°C
+ Supply Voltage (VDD) = 3.3V
+ Line Regulation = 77mV/V
+ Temperature Coefficient (TC) =	19ppm/°C

# Circuit 2: Op-Amp-Based Bandgap Reference

This design enhances the bandgap reference by incorporating a feedback op-amp, improving current matching, loop stability, and temperature compensation.
Compared to the current-mirror-based design, this architecture provides better reduced supply variation.
![](https://github.com/Ganesh11062004/Band_gap_reference_ckt_Sub_1_volt/blob/65724329e82c10e639391d6a2c5a0a02bfa5d60e/schematic_ckts/bgr_opamp.png)

### Performance Summary
+ Reference Voltage (Vref) = 1.22V at 27°C
+ Supply Voltage (VDD) = 3.3V
+ Line Regulation = 3.9mV/V
+ Temperature Coefficient (TC) =	28.6ppm/°C

# Circuit 3: Sub-1 V CMOS Bandgap Reference

This circuit is an optimized sub-bandgap reference designed to operate below the classical 1.2 V limit, making it suitable for low-power and low-supply SoC applications.
The architecture achieves a 0.75 V reference voltage while maintaining acceptable temperature stability and supply regulation.

![](https://github.com/Ganesh11062004/Band_gap_reference_ckt_Sub_1_volt/blob/65724329e82c10e639391d6a2c5a0a02bfa5d60e/schematic_ckts/bgr_sub_1.png)

### Performance Summary
+ Reference Voltage (Vref) =	0.7506V at 27°C
+ Supply Voltage (VDD) = 3.3V
+ Line Regulation = 1.75mV/V
+ Temperature Coefficient (TC) =	16.5ppm/°C

## What Is the Zero-Current State?
A bandgap reference is a self-biased circuit, meaning it generates its own bias currents internally, no external bias source forces current at power-up.
Because of this, the BGR mathematically allows more than one DC operating point.
### Zero-Current State (Undesired)
- All branch currents = 0
- MOSFETs are OFF
- BJTs are OFF (V_BE ≈ 0)
- Output reference voltage = 0 V
  
This zero-current condition satisfies KCL and KVL, so it is a valid equilibrium point of the circuit.

Due to the self-biased nature of bandgap reference circuits, an undesired zero-current operating point exists in which all transistors remain off and no reference voltage is generated. At power-up, the circuit may settle into this equilibrium and fail to start. A startup circuit is therefore employed to inject a small temporary bias current during power-up, forcing the circuit away from the zero-current state and enabling the establishment of the intended PTAT and CTAT currents. Once normal operation is achieved, the startup circuit automatically disables itself, ensuring no impact on steady-state performance.
