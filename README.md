# IR-Remote-Controlled-Latching-Light-Switch-Using-555-Timers
This project implements a microcontroller-free IR remote controlled ON/OFF switch using two NE555 timers.

A microcontroller-free IR remote controlled ON/OFF switch implemented using two NE555 timers. The circuit converts the pulse burst from a standard IR receiver into a single trigger pulse, allowing a bistable 555 timer to toggle its output once for every remote button press.

---

## Overview

IR receiver modules generate a burst of pulses whenever a remote button is pressed. Feeding these pulses directly to a bistable circuit causes multiple unwanted toggles. This project solves the problem by introducing a monostable stage that converts the entire IR burst into a single pulse before driving the bistable stage.

The design requires no microcontroller, making it simple, low-cost, and easy to implement.

---

## Working Principle

1. The IR receiver detects a button press and outputs a burst of active-low pulses.
2. The first falling edge triggers a 555 timer configured as a monostable multivibrator.
3. The monostable generates a single pulse of approximately **250 ms**, which is longer than the measured IR burst duration.
4. This pulse is applied to a second 555 timer configured as a bistable multivibrator.
5. The bistable changes its state once for every valid button press, allowing the connected load to toggle ON and OFF.

---

## Block Diagram

```
IR Remote
     │
     ▼
IR Receiver
     │
     ▼
555 Monostable
 (250 ms Pulse)
     │
     ▼
555 Bistable
 (Toggle Latch)
     │
     ▼
Relay / Load
```

---

## Measured IR Burst Durations

| Remote | Burst Duration |
|---------|---------------:|
| LG TV | 68.54 ms |
| Samsung TV | 68.54 ms |
| LG Repeat Frame | 11.75 ms |
| Other IR Remote | ~200 ms |

The monostable pulse width was selected as approximately **250 ms** to ensure a single output pulse for every button press, independent of the IR protocol.

---

## Features

- Microcontroller-free design
- Single toggle per button press
- Compatible with standard 38 kHz IR receiver modules
- Supports different IR remote protocols
- Designed and verified using LTspice
- PCB designed in EasyEDA

---


## Future Improvements

- Relay driver stage for higher power loads
- Compact PCB revision
- Battery-powered version
- Hardware implementation and testing

---

## License

This project is licensed under the MIT License.
