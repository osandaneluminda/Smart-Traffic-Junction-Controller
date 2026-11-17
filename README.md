Smart Traffic Junction Controller 

## Project Overview

The Smart Traffic Junction Controller is a microcontroller-based traffic management system developed using the **ATmega328P microcontroller** and programmed in **AVR Assembly language**.

The system controls traffic signals at a four-way junction and includes pedestrian crossing functionality, a countdown display, and automatic night-mode operation using a Light Dependent Resistor (LDR).

This project demonstrates practical applications of embedded systems, low-level programming, hardware timers, interrupts, ADC conversion, and digital input/output control.

## Features

- **Automatic Traffic Control:** Alternates traffic signals between North-South and East-West directions.
- **Pedestrian Crossing:** Detects pedestrian requests using a push button.
- **Pedestrian Safety:** Provides an all-red clearance interval before pedestrian crossing.
- **Countdown Display:** Displays the pedestrian countdown from 5 to 0 using a seven-segment display.
- **Automatic Night Mode:** Detects low ambient light using an LDR sensor.
- **Yellow Light Flashing:** Flashes both yellow traffic signals during night mode.
- **Brightness Confirmation:** Requires sustained bright readings before returning to normal operation.
- **Timer Interrupts:** Uses Timer1 in CTC mode to generate a 1 ms timing reference.

## Hardware Components

| Component | Purpose |
|---|---|
| Arduino Uno / ATmega328P | Main microcontroller |
| 6 LEDs | Traffic signal indicators |
| Push Button | Pedestrian request input |
| LDR Sensor | Ambient light detection |
| Common-Anode 7-Segment Display | Pedestrian countdown |
| Resistors | Current limiting and voltage divider |
| Breadboard and Jumper Wires | Circuit connections |

## Pin Configuration

| Function | ATmega328P Pin | Arduino Pin |
|---|---|---|
| North-South Red | PD2 | D2 |
| North-South Yellow | PD3 | D3 |
| North-South Green | PD4 | D4 |
| East-West Red | PD5 | D5 |
| East-West Yellow | PD6 | D6 |
| East-West Green | PD7 | D7 |
| Pedestrian Button | PC0 | A0 |
| LDR Sensor | PC1 / ADC1 | A1 |
| Seven-Segment A–D | PC2–PC5 | A2–A5 |
| Seven-Segment E | PB0 | D8 |
| Seven-Segment G | PB2 | D10 |
| Seven-Segment F | PB3 | D11 |

## Traffic Signal Sequence

The normal traffic cycle consists of four phases:

1. North-South Green / East-West Red – 3 seconds
2. Both Yellow – 1.5 seconds
3. East-West Green / North-South Red – 3 seconds
4. Both Yellow – 1.5 seconds

## Pedestrian Crossing Operation

1. The controller detects a pedestrian button press.
2. The request is stored using a software flag.
3. The current traffic phase completes its required transition.
4. Both vehicle directions receive red signals.
5. A 1-second all-red clearance interval is provided.
6. The seven-segment display shows the countdown from 5 to 0.
7. Normal traffic operation resumes.

## Automatic Night Mode

The LDR sensor measures ambient light through ADC1.

- ADC reading below 100: Dark condition.
- ADC reading at or above 100: Bright condition.
- Both yellow traffic lights flash with 500 ms ON and 500 ms OFF intervals during night mode.
- Ten consecutive half-second bright readings are required before leaving night mode.

The ADC threshold should be calibrated according to the actual LDR circuit and lighting conditions.

## Software and Tools

- AVR Assembly Language
- ATmega328P Microcontroller
- Arduino Uno
- AVR Assembly development environment
- Proteus (if used for simulation)

## Key Embedded Systems Concepts

- GPIO configuration using DDR and PORT registers
- Timer1 CTC mode
- Compare-match interrupts
- ADC configuration and conversion
- Seven-segment display interfacing
- Push-button input handling
- Software flags and timing routines
- Embedded system state-machine design

## Project Documentation

The project report includes:

- Hardware design and circuit schematic
- Pin-to-port mapping
- Firmware architecture
- System state machine
- Firmware flowcharts
- Traffic phase design
- Implementation details
- Testing and results

## Project Team

Developed as part of the Embedded Systems Engineering (IE3064) assignment at **Sri Lanka Institute of Information Technology (SLIIT)**.

## Future Improvements

- Improve traffic transition timing and safety verification.
- Calibrate the LDR threshold using actual environmental measurements.
- Verify seven-segment display mapping and countdown timing.
- Improve pedestrian request handling and overall system reliability.

---

Note: This project is an academic embedded systems prototype and is not certified for use in real-world traffic control systems.