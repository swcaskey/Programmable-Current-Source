# Programmable Current Source

An adjustable, precision current source designed for test bench and calibration use.

## Overview
This project implements a programmable constant-current source using **operational amplifiers**, a **MOSFET driver stage**, and **Arduino-based DAC control**.  
It allows user-defined current settings via the Arduino Serial Monitor and regulates output through a feedback loop.

- **Output Range:** 0 – 10 mA  
- **Setpoint Resolution:** 0.5 mA  
- **Regulation Accuracy:** ±0.25 mA  
- **Voltage Limit:** 15 V  

## Design Concept
- **Architecture:** OP-AMP–MOSFET feedback topology with a precision current-sense resistor.  
- **Control Logic:** Arduino generates a voltage reference (DAC output) proportional to the user’s desired current.  
- **Feedback Loop:** The op-amp adjusts the MOSFET gate voltage to maintain constant current through the load.  
- **Measurement:** The Arduino measures voltage across the sense resistor (≤1 Ω) via ADC for closed-loop feedback.  
- **Simulation:** Verified circuit behavior and linearity in **LTSpice** and **AutoDesk (TinkerCAD web) Arduino Sim** prior to hardware testing.

## Testing and Validation
- Tested across multiple resistive loads (24 Ω – 1.3 kΩ) and an LED & IDE terminal to validate constant-current behavior.  
- Measured stability and response with oscilloscope and multimeter.
- Observed accurate regulation across full output range (0–10 mA).  
- System remained stable for supply voltages between 5–15 V. 

## Challenges and Iteration
- Initial issues with DAC bit alignment caused inaccurate current regulation.  
- Resolved by debugging PWM-to-voltage scaling in simulation and hardware.  
- Explored loop timing effects — discovered that faster load changes (≥100 Hz) exceeded the control loop’s update rate.  

## Documentation
Testing photos, schematic captures, and performance data:  
- [Google Photos Album](https://photos.app.goo.gl/ThNHLy9iuzCLFQ5C7)
- [Writeup](https://docs.google.com/document/d/109mvFCIYR1HQHMP3YRnqCsOd_dF2gdiRvDrdnpQr6D8/edit?usp=sharing)

## Author
Created by **Seth Caskey** — Rutgers University, 2024.
