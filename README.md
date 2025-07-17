# SRAM Design Project

**Authors:** Aishwarya Bommireddipalli, Albert DiCroce, Alexandra Wright, Stephen Singh  
**Department of Electrical and Computer Engineering, University of Florida** :contentReference[oaicite:0]{index=0}

---

## Table of Contents

- [Abstract](#abstract)  
- [Introduction](#introduction)  
- [Design Components](#design-components)  
  - [SRAM Cell](#sram-cell)  
  - [Row and Column Decoders](#row-and-column-decoders)  
  - [Read/Write Control](#readwrite-control)  
  - [Sense Amplifier](#sense-amplifier)  
- [Simulations](#simulations)  
  - [Setup](#setup)  
  - [Pre-charge](#pre-charge)  
  - [Read and Write Operations](#read-and-write-operations)  
- [Layout](#layout)  
- [Conclusion](#conclusion)  
- [References](#references)  
- [Work Contributions](#work-contributions)  

---

## Abstract

This project presents the design and implementation of a custom 8×4 Static Random Access Memory (SRAM) cell at the 45 nm technology node, including all supporting circuitry and full-chip layout. We discuss the transistor-level components, decoder logic, sense amplification, and read/write control, then validate functionality through transient simulations in Cadence ADE L. :contentReference[oaicite:1]{index=1}

## Introduction

SRAM is widely used for its low power consumption and fast access times in SoCs for smartphones, laptops, and other high-density applications. A standard 6-transistor (6T) cell stores one bit, accessed via row (word line) and column (bit line) decoders. This design explores an 8-row by 4-column array, detailing each subcircuit and verifying performance through simulation. :contentReference[oaicite:2]{index=2}

## Design Components

### SRAM Cell

- **6T Cell Structure:** Two cross-coupled inverters form a bistable latch.  
- **Access Transistors:** Controlled by the word line to enable read/write.  
- **Bit Lines:** Complementary pairs sense or drive cell states.

### Row and Column Decoders

- **Row Decoder (3-to-8):** Translates 3-bit address input to eight word lines.  
- **Column Decoder:** Selects one of four bit-line pairs for read/write access.

### Read/Write Control

- **Enable Signals:** Separate read-enable and write-enable inputs.  
- **Logic Gates:** AND-gate based control to pre-charge bit lines and activate sense amplifier or drive cell inputs for writing.

### Sense Amplifier

- **Differential Amplifier:** Detects small voltage differences (hundreds of millivolts) between bit lines.  
- **Output Buffering:** Amplifies to full logic levels for reliable readout.

## Simulations

### Setup

- **Tool:** Cadence ADE L transient simulations.  
- **Stimuli:** Pulsed read/write enables, address toggling, and clock drives.  
- **Validation:** Individual blocks tested before full-array integration. :contentReference[oaicite:3]{index=3}

### Pre-charge

- **Bit Line Pre-charge:** Bit lines are driven to VDD prior to read to minimize delay.  
- **Clock-controlled Pre-charge:** Ensures consistent timing for read operations.

### Read and Write Operations

- **Write ‘1’/‘0’:** Drive one bit line high, the other low, assert word line.  
- **Read:** Pre-charge bit lines, assert word line, sense line pulled low indicating stored bit.  
- **Verification:** Transient waveforms confirm correct logic levels at various addresses.

## Layout

- **Technology:** GPDK 45 nm node.  
- **Hierarchy:**  
  - Bit-cell layouts verified with DRC/LVS.  
  - Decoders and sense amplifier laid out using standard cell methodology.  
- **Metal Routing:** Power rails (VDD/VSS) on metal layers; bit lines on Metal-1; gates on polysilicon. :contentReference[oaicite:4]{index=4}

## Conclusion

The 8×4 SRAM design demonstrates correct functionality and layout compliance at 45 nm. Future enhancements could include capacity scaling, frequency optimization, and additional sense-amplifier channels to accommodate larger arrays.

## References

1. J. IMP, “VLSI Memory,” University of New Mexico, 2022. :contentReference[oaicite:5]{index=5}

## Work Contributions

- **Aishwarya Bommireddipalli:** Schematic design, full-array verification.  
- **Albert DiCroce:** Column decoder layout and reporting.  
- **Alexandra Wright:** 8×4 SRAM layout integration.  
- **Stephen Singh:** Bit-cell layout, DRC/LVS verification of sense amplifier, row decoder layout. :contentReference[oaicite:6]{index=6}  
