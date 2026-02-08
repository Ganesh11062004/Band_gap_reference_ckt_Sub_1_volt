## CMOS Bandgap Reference Circuits – UMC 180 nm

This repository contains the design, implementation, and simulation of three CMOS Bandgap Reference (BGR) circuits developed in UMC 180 nm technology.
The objective of this project is to analyze temperature stability, supply sensitivity, and low-voltage operation, and to compare different BGR architectures.

All circuits were designed and verified using Cadence Virtuoso with DC, temperature sweep, and supply variation simulations.

# Circuit 1: Current-Mirror-Based Bandgap Reference
### Description

This design implements a classical current-mirror-based bandgap reference, combining PTAT and CTAT components to generate a temperature-compensated reference voltage.
The circuit serves as a baseline architecture and highlights the limitations of mirror-only designs in terms of temperature sensitivity and supply dependence.

# Performance Summary
+ Reference Voltage (Vref) = 1.28V at 27°C
+ Supply Voltage (VDD) = 3.3V
+ Line Regulation = 77mV/V
+ Temperature Coefficient (TC) =	19ppm/°C

# Circuit 2: Op-Amp-Based Bandgap Reference
Description

This design enhances the bandgap reference by incorporating a feedback op-amp, improving current matching, loop stability, and temperature compensation.
Compared to the current-mirror-based design, this architecture provides better reduced supply variation.

+ Performance Summary
+ Reference Voltage (Vref) = 1.22V at 27°C
+ Supply Voltage (VDD) = 3.3V
+ Line Regulation = 3.9mV/V
+ Temperature Coefficient (TC) =	28.6ppm/°C

# Circuit 3: Sub-1 V CMOS Bandgap Reference
Description

This circuit is an optimized sub-bandgap reference designed to operate below the classical 1.2 V limit, making it suitable for low-power and low-supply SoC applications.
The architecture achieves a 0.75 V reference voltage while maintaining acceptable temperature stability and supply regulation.

+ Performance Summary
+ Reference Voltage (Vref) =	0.7506V at 27°C
+ Supply Voltage (VDD) = 3.3V
+ Line Regulation = 1.75mV/V
+ Temperature Coefficient (TC) =	16.5ppm/°C
