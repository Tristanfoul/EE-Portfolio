# 4-Bit & 8-Bit Binary Adder — Schematic Entry (Quartus II)

**Course:** ELEN 305: Digital Logic Design Lab  
**Semester:** Spring 2026  
**Tools:** Quartus II, Altera DE2 Board (Cyclone II EP2C35F672C6)  
**Submitted to:** Dr. Arasteh

---

## Overview

This project involves the design, implementation, simulation, and verification of a **4-bit and 8-bit binary adder** using schematic entry (Block Design File) in Quartus II. Rather than building from individual gates, the design uses the pre-defined **74283** 4-bit full-adder IC symbol from the Quartus II library — a single-chip adder with built-in carry-lookahead logic.

The 8-bit adder was constructed by cascading two 74283 ICs, connecting the carry-out (COUT) of the lower 4-bit adder to the carry-in (CIN) of the upper 4-bit adder.

---

## Part 1 — Four Bit Adder

### Design
The 4-bit adder computes `A[3..0] + B[3..0]` and produces:
- A 4-bit sum output: `SUM[3..0]`
- A carry-out bit: `COUT`
- CIN tied to GND (logic 0) for standard operation

### Block Diagram Schematic
The schematic was created as a Block Design File (`fourbit.bdf`) in Quartus II using the 74283 symbol with labeled input and output buses.

![4-Bit Adder Schematic](./images/fourbit_schematic.jpg)

### Functional Simulation
A Vector Waveform File (`fourbit.vwf`) was created to test at least 8 input combinations. The simulation verified correct sum and carry-out values across all tested cases.

- Simulation coverage: 92.50%
- Transitions in simulation: 208
- Result: **0 errors, 0 warnings**

![4-Bit Simulation Waveforms](./images/fourbit_waveform.jpg)

---

## Part 2 — Eight Bit Adder

### Design
The 8-bit adder extends the 4-bit design by cascading two 74283 ICs:
- Lower IC handles bits `A[3..0]` and `B[3..0]`
- Upper IC handles bits `A[7..4]` and `B[7..4]`
- COUT of lower adder connects to CIN of upper adder for carry propagation
- Final output: `SUM[7..0]` and `COUT`

### Block Diagram Schematic
The schematic (`eight.bdf`) shows both 74283 ICs connected in cascade with properly labeled input/output buses.

![8-Bit Adder Schematic](./images/eightbit_schematic.jpg)

### Functional & Timing Simulation
Both functional and timing simulations were run using a Vector Waveform File (`eight.vwf`). The simulations confirmed correct addition results across all tested input combinations.

- Logic Cells used: 17
- Simulation coverage: 100%
- Transitions in simulation: 247
- Result: **0 errors, 0 warnings**

![8-Bit Functional Simulation](./images/eightbit_functional_waveform.jpg)
![8-Bit Timing Simulation](./images/eightbit_timing_waveform.jpg)

---

## Key Concepts Demonstrated

| Concept | Application |
|---------|-------------|
| Bus notation | A[3..0], B[3..0], SUM[3..0] |
| TTL component symbols | 74283 4-bit full adder |
| Input/output port placement | Labeled INPUT/OUTPUT symbols in BDF |
| Carry propagation | COUT of lower → CIN of upper adder |
| Functional simulation | Vector waveform testing of 8+ cases |
| Timing simulation | Verified propagation delay behavior |

---

## Key Takeaways

- Schematic entry in Quartus II allows complex digital systems to be built from pre-defined IC symbols without manual gate-level design
- Cascading two 4-bit adders to form an 8-bit adder demonstrates how carry propagation works across larger word widths
- Both functional and timing simulations are important — functional confirms logic correctness while timing reveals real propagation delays
- The 74283's built-in carry-lookahead logic makes it significantly faster than a ripple carry adder of the same width

---

## Files
```
/
├── README.md
├── fourbit.bdf
├── fourbit.vwf
├── eight.bdf
├── eight.vwf
└── images/
    ├── fourbit_schematic.jpg
    ├── fourbit_waveform.jpg
    ├── eightbit_schematic.jpg
    ├── eightbit_functional_waveform.jpg
    └── eightbit_timing_waveform.jpg
```
